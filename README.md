# MCMC-chain 

This project is to impiment the Metropolis-Hastings algorithm and the Affine-invariant ensemble MCMC for sampling 6 parameters of the LCDM model under idealized data.


The cosmic microwave background (CMB) is electromagnetic radiation as a remnant from an early stage of the universe in the standard cosmology. The use of CMB observation enables us to explore the evolution of the Universe and temperatures at all angular positions are measured for this study. There are 6 parameters which descibe the evolution of the cosmic structure and the paramters with relavant physical models constraint the angular distribution of temperature. The cosmological parameters are:
> - **Ω_b**: density of baryonic matter
> - **Ω_cdm**: density of cold dark matter (cdm)
> - **τ_reio**: optical depth at the epoch of reionization
> - **θ_s**: the angular scale of the sound horizon at matter-radiation equality
> - **A_s**: curvature perturbations
> - **n_s**: scalar spectral index.

In this notebook, I will show how to sample the cosmological (LCDM) parameters using two MCMC methods.
