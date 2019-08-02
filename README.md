# MCMC-chain

# Choosing proposal density, $P_\text{prop} (\vec{p}|\vec{p}_\text{curr})$
If one has an idea of the posterior, covariance matrix, and linearity of parameters, a typical choice is:
$$\begin{align*}
\mathcal{P}_\text{prop}(\vec{p}|\vec{p}_\text{curr})\sim \mathcal{N}(\vec{p}_\text{curr}, g\Sigma)
\end{align*}$$
where $g$ is called "$g$-prior" which is tuned to get a good acceptance rate.

1. Linear regression
> If our data model is approximated as:
$$\begin{align*}
\vec{y} & = {\mathbf X}\cdot \vec{\beta} + \vec{\large \epsilon}\\
& = \nabla_\vec{p}C_l^{TT,\vec{p}} \cdot (\vec{p}-\vec{p}_0) + C_l^{\epsilon\epsilon}
\end{align*}$$
where 
${\mathbf X} \rightarrow \nabla_\vec{p}C_l^{TT,\vec{p}}$, $\vec{\beta} \rightarrow \vec{p}-\vec{p}_0$, and 
$\vec{\large \epsilon} \rightarrow Std(\sigma_l)$. 
>
Then, the best estimate of $\vec{\beta}$, i.e., $\hat{\beta}$ is such that:
$$\begin{align*}
\hat{\beta}=  \underset{\vec{b}}{\arg\min}\bigg[
(\vec{y}-{\mathbf X}\cdot\vec{b})^{\intercal}\Omega^{-1}(\vec{y}-{\mathbf X}\cdot\vec{b})
\bigg]
\end{align*}$$
where $E({\large \epsilon}|{\mathbf X}) = 0$, and ${\rm Cov}({\large \epsilon}|{\mathbf X}) = \Omega$; 
the conditional variance of the error term given ${\mathbf X}$ is a known nonsingular matrix ${\mathbf{\Omega}}$. 
$\hat{\beta}$ is estimated by minimizing 
$(\vec{y}-{\mathbf X}\cdot\vec{b})^{\intercal}\Omega^{-1}(\vec{y}-{\mathbf X}\cdot\vec{b})$: 
$$\begin{align*}
\frac{\rm d}{{\rm d}\vec{b}}
\bigg\{(\vec{y}-{\mathbf X}\cdot\vec{b})^{\intercal}\Omega^{-1}(\vec{y}-{\mathbf X}\cdot\vec{b})
\bigg\} = 0.
\end{align*}$$
By solving the equation above, we have:
$\vec{b}=\hat{\beta}=({\mathbf X}^{\intercal}
\Omega^{-1}{\mathbf X})^{-1}{\mathbf X}^{\intercal}\Omega^{-1}\vec{y}$, the best linear unbiased estimator for
$\vec{\beta}$.

2. Estimating $\vec{\beta}$ for a finite sample distribution
>Assuming $\vec{\large \epsilon}\sim\mathcal{N}(0,g\Omega)$, we have:
$$
\begin{align*}
\hat{\beta}&=({\mathbf X}^{\intercal}\Omega^{-1}{\mathbf X})^{-1}{\mathbf X}^{\intercal}\Omega^{-1}\vec{y}
\ \ \ \  \text{where}\ \vec{y}={\mathbf X}\cdot\vec{\beta}+\vec{\large \epsilon}\\
&= \vec{\beta} + {\mathbf X}^{-1}\vec{\large \epsilon}\\
&\ \ \ \ \  \underline{\rm note}\ \  \vec{x} \sim \mathcal{N}(\vec{\mu},\sigma^2= \Sigma)\ \ \ 
\text{where } \Sigma=U\Lambda U^{\intercal}= (U\Lambda^{1/2})(U\Lambda^{1/2})^{\intercal}\\
&\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \  = \vec{\mu} + U\Lambda^{1/2}\mathcal{N}(0,I) \ \ \  
\text{where }\ U:\text{orthogonal matrix},\  \Lambda: \text{diag. matrix w/ positive definite (similarity trans.)}\\
&= \vec{\beta} + {\mathbf X}^{-1}\mathcal{N}(0,g\Omega)\\
&=\mathcal{N}(\vec{\beta},g({\mathbf X}^{\intercal}\Omega^{-1}{\mathbf X})^{-1})
\end{align*}
$$
$\therefore \hat{\beta}\sim\mathcal{N}(\vec{\beta},g({\mathbf X}^{\intercal}\Omega^{-1}{\mathbf X})^{-1})$

3. Applying this to our data
> Now the proposal density is estimated as follows:
$$
\begin{align*}
\mathcal{P}_\text{prop}(\vec{p}~|~\vec{p}_\text{curr})
&\sim \mathcal{N}(\vec{p}_\text{curr}, g\Sigma)
= \mathcal{N}(\vec{p}_\text{curr},g ({\mathbf X}^{\intercal}\Omega^{-1}{\mathbf X})^{-1}))\\
&= \mathcal{N}(\vec{p}_\text{curr},g ({\mathbf X}^{\intercal}\Omega^{-1}{\mathbf X})^{-1}))\\
&= \mathcal{N}\bigg(\vec{p}_\text{curr},~g\bigg\{(\nabla_\vec{p}C_l^{TT,\vec{p}})^{\intercal} 
\bigg(\frac{2}{2l+1}(C_l^{TT,\vec{p}}+C_l^{\epsilon\epsilon})^2\bigg)^{-1}(\nabla_\vec{p}C_l^{TT,\vec{p}})
\bigg\} \bigg)
\end{align*}
$$
