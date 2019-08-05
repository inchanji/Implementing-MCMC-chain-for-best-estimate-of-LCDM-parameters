# MCMC-chain 

This project is to impiment the Metropolis-Hastings algorithm and the Affine-invariant ensemble MCMC for sampling 6 parameters of the LCDM model under idealized data.


The cosmic microwave background (CMB) is electromagnetic radiation as a remnant from an early stage of the universe in the standard cosmology. The use of CMB observation enables us to explore the evolution of the Universe and temperatures at all angular positions are measured for this study. There are 6 parameters which descibe the evolution of the cosmic structure and the paramters with relavant physical models constraint the angular distribution of temperature. The cosmological parameters are:
> - **Ω_b**: density of baryonic matter
- **Ω_cdm**: density of cold dark matter (cdm)
- **τ_reio**: optical depth at the epoch of reionization
- **θ_s**: the angular scale of the sound horizon at matter-radiation equality
- **A_s**: curvature perturbations
- **n_s**: scalar spectral index.



The finite-dimensional distribution (hearafter f.d.d. data is discretely spaced in the units of pixel) of cosmic temperature follow a Gaussian random process. The observed data consist of: 
\begin{aligned}
\vec{\rm d}~({\rm =}~ d(\hat{n})) = T(\hat{n}) + \mathcal{E}(\hat{n}) 
\end{aligned}
where $\vec{\rm d}$(or d($\hat{n}$)) is data , T($\hat{n}$) $\sim (0,\Sigma^{TT}(\vec{p}))$ is model temperature, $\mathcal{E}$($\hat{n}$) $\sim (0,\Sigma^{\mathcal{EE}})$ is noise bias, and $\hat{n}$ is angular position vector. 

Acutally, the temperature we observe is PSF-convolved one. Therefore, <br>
\begin{aligned}
&~d(\hat{n}) = \phi * T(\hat{n}) + \mathcal{E}(\hat{n}) ~ :{\rm general~expression}\\
\Longleftrightarrow &~d_{lm} = (\phi * T)_{lm} + \mathcal{E}_{lm} ~~~ :{\rm expressed~in~spherical~harmonics~on~S}^2
\end{aligned}              
where $\phi$ is a Gaussian beam PSF on $S^2$.

Dividing by the beam and renaming $d_{lm}~\&~\mathcal{E}_{lm}$ gives a general model for observation:
\begin{aligned}
d_{lm} = T_{lm} + \mathcal{E}_{lm} ~~~ {\rm for~}l={\rm 0,1,2,\cdots,~and~}m=-l,-l+1,\cdots,l-1,l
\end{aligned}     
where $E(T_{lm}\cdot\overline{T_{l'm'}})=\delta_{ll'}\delta_{mm'}C_l^{TT}$,
$E(\mathcal{E}_{lm}\cdot\overline{\mathcal{E}_{l'm'}})=\delta_{ll'}\delta_{mm'}C_l^{\mathcal{EE}}
= \delta_{ll'}\delta_{mm'}\sigma^2\exp\bigg(\frac{b^2}{8\ln 2}l(l+1)\bigg)$, $\sigma$ is addictive noise level, and $b$ is FWHM of the PSF.
