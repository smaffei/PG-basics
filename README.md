# PG-basics

Mathematical and numerical development of a Plesio Geostrophic model for Earth's core.

The present repository contains Mathematica notebooks that reproduce results from Maffei et al., 2024, submitted to GJI.

## Assumptions and governing equations
Plesio-geostrophy (PG) is a columnar-flow description of the dynamics of Earth's fluid core. It is predicated upon the assumption that the fluid velocity $\textbf{u}$ can be described via the following columnar-flow ansatz (Schaeffer & Cardin, 2005):

$$
\textbf{u}(s,\phi,z) = \frac{1}{H}\nabla\times(\Psi\hat{\bf z}) - \frac{z}{H^3}\frac{\partial \Psi}{\partial \phi} \hat{\bf z}, 
$$
where cylindircal coordinates $(s,\phi,z)$ are used and $\Psi(s,\phi)$ is a pseudo-streamfunction.

The present version of the PG model considers a rotating full sphere, with radius $r_o$, filled with an internally heated Boussinesq fluid. Magnetic effects are ignored. The non-dimensional equations governing the evolution of velocity $\textbf{u}$ and temperature perturbation $T$ are:

$$
\begin{split}
\frac{\partial \textbf{u}}{\partial t} + 2\hat{\bf z}\times\textbf{u} + \nabla p &= 2E (Ra T \textbf{r} + \nabla^2 \textbf{u}),\\
Pr \frac{\partial T}{\partial t} = \textbf{u}\cdot\textbf{r}& + 2E \nabla^2 T,
\end{split}
$$
where $p$ is the dynamic pressure and $E$ and $Pr$ are, respectively, the Ekman and the thermal Prandtl numbers:
$$E = \frac{\nu}{2 \Omega r_o^2},$$
$$Pr = \frac{\nu}{\kappa},$$
and $Ra$ is the Rayleigh number, defined as
$$Ra =  \frac{\alpha \chi \gamma r_o^4}{\Omega \kappa}$$

In the above $\nu$ is the kinematic viscosity, $\Omega$ is the rotation rate of the sphere, $\kappa$ is the thermal diffusivity, $\alpha$ is the thermal expansion coefficient, $\chi$ is the background temperature gradient and $\gamma$ is the gravity acceleration. All of these quantites are considered constant.

**Note that the above nondimensionalisation is not the same as the one employed in Maffei et al., 2024, but it is the one employed in Zhang & Liao, 2004. It is straightforward to convert both $E$ and $Ra$ to the definitions of Maffei et al., 2024.**



## Repository content

The Mathematica notebook ``PG_convection_onset.nb`` computes 

## References

Maffei, S., Jackson, A. & Livermore, P. W., 2024. Plesio-Geostrophy for Earth's core II: Onset of Thermal Convection. *Submitted to GJI*.

Schaeffer, N. & Cardin, P., 2005. Quasi-Geostrophic Model of the Instabilities of the Stewartson Layer, *Phys. Fluids*, **17**, 104–111.

Zhang, K. & Liao, X., 2004. A new asymptotic method for the analysis of convection in a rapidly rotating sphere, *Journal of Fluid Mechanics*, **518**, 319–346.