# PG-basics

Mathematical and numerical development of a Plesio Geostrophic model for Earth's core.

The present repository contains Mathematica notebooks that reproduce results from Maffei et al., 2024, submitted to GJI.

## Assumptions and governing equations
Plesio-geostrophy (PG) is a columnar-flow description of the dynamics of Earth's fluid core. It is predicated upon the assumption that the fluid velocity $\textbf{u}$ can be described via the following columnar-flow ansatz (Schaeffer & Cardin, 2005):

$$
\textbf{u}(s,\phi,z) = \frac{1}{H}\nabla\times(\Psi\hat{\bf z}) - \frac{z}{H^3}\frac{\partial \Psi}{\partial \phi} \hat{\bf z}, \quad (1)
$$
where cylindircal coordinates $(s,\phi,z)$ are used and $\Psi(s,\phi)$ is a pseudo-streamfunction.

The present version of the PG model considers a rotating full sphere, with radius $r_o$, filled with an internally heated Boussinesq fluid. Magnetic effects are ignored. The non-dimensional equations governing the evolution of velocity $\textbf{u}$ and temperature perturbation $T$ are:

$$
\begin{split}
\frac{\partial \textbf{u}}{\partial t} + 2\hat{\bf z}\times\textbf{u} + \nabla p &= 2E (Ra T \textbf{r} + \nabla^2 \textbf{u}),\quad (2)\\
Pr \frac{\partial T}{\partial t} = \textbf{u}\cdot\textbf{r}& + 2E \nabla^2 T, \quad (3)
\end{split}
$$
where $p$ is the dynamic pressure and $E$ and $Pr$ are, respectively, the Ekman and the thermal Prandtl numbers:
$$E = \frac{\nu}{2 \Omega r_o^2},$$
$$Pr = \frac{\nu}{\kappa},$$
and $Ra$ is the Rayleigh number, defined as
$$Ra =  \frac{\alpha \chi \gamma r_o^4}{\Omega \kappa}$$

In the above $\nu$ is the kinematic viscosity, $\Omega$ is the rotation rate of the sphere, $\kappa$ is the thermal diffusivity, $\alpha$ is the thermal expansion coefficient, $\chi$ is the background temperature gradient and $\gamma$ is the gravity acceleration. All of these quantites are considered constant.

**Note that the above nondimensionalisation is not the same as the one employed in Maffei et al., 2024, but it is the one employed in Zhang & Liao, 2004. It is straightforward to convert both $E$ and $Ra$ to the definitions of Maffei et al., 2024.**

The plesio-geostrophic model equations are obtained by manipulating the governing equations (2)-(3) as described in Jackson & Maffei, 2020 and Maffei et al., 2024. The resulting system of equations describes the evolution of the PG variables $\Psi$, $\overline{T}$ and $\widetilde{zT}$, where

$$\overline{T} = \int_{-H}^{H} T \,dz,$$
and
$$\widetilde{zT}=\int_{-H}^H \textrm{sgn}(z) zT\,dz.$$

The linearised PG system of equation is:
$$
\begin{split}
    \left[-\frac{\partial}{\partial s} \left(\frac{s}{H} \frac{\partial}{\partial s}\right) -\frac{1}{H}\left( \frac{s}{2H^2}+\frac{1}{s}\right)\frac{\partial^2}{\partial \phi^2}\right] \frac{\partial \Psi}{\partial t} &= \frac{s }{2H}\left( F_C + 2 E Ra F_T + 2 E F_V\right),\\
%
    \frac{\partial \overline{T}}{\partial t} =   \frac{1}{Pr}\frac{4}{3}sHu_s + &\frac{E}{Pr}  H\nabla_e^2 \left(\frac{\overline{T}}{H}\right),\\
%
    \frac{\partial \widetilde{zT}}{\partial t} =  \frac{1}{Pr}\frac{1}{2}sH^2u_s &+ \frac{E}{Pr}H^2 \nabla_e^2 \left( \frac{\widetilde{z T}}{H^2} \right).
\end{split}
$$
In the above, $F_A$, $F_C$, $F_T$ and $F_V$ indicate the PG forcing derived from, respectively, the non-linear advection term, the Coriolis force, buoyancy and viscous dissipation.

The PG equations are solved via a fully-spectral, Galerkin methodology.

Full details are available in Jackson & Maffei, 2020 and Maffei et al., 2024.

## Repository content

- The Mathematica notebook ``PG_convection_onset.nb`` implements the methodology to find the critical Rayleigh, $Ra_c$ and  drift frequency $\omega_c$ for a given azimuthal wavenumber $m_c$ at the onset of thermal convection. Enough information should be given in the notebook itself to be able to successfully run the it.

- In the folder ``Matrices``, the matrices for the case $m_c=1$ and spectral truncation $N=15$ are already given and can be loaded by the Mathematica notebook without the need to recalculate them. Matrices for different spatial resolution and azimuthal wavenumbers, calcualted with the notebook, will be saved in the same folder.

The notebook has been tested with Mathematica version 12 on a MacBook Pro with OS Ventura 13.3.1. 

In case of any issues, do not hesitate to contact Dr. Stefano Maffei at maffei.ste@gmail.com or stefano.maffei@erdw.ethz.ch .

## References

Jackson, A. & Maffei, S., 2020. Plesio-geostrophy for earth’s core: I. basic equations, inertial modes and induction, *Proceedings of the Royal Society A: Mathematical, Physical and Engineering Sciences*, **476**(2243), 20200513.

Maffei, S., Jackson, A. & Livermore, P. W., 2024. Plesio-Geostrophy for Earth's core II: Onset of Thermal Convection. *Submitted to GJI*.

Schaeffer, N. & Cardin, P., 2005. Quasi-Geostrophic Model of the Instabilities of the Stewartson Layer, *Phys. Fluids*, **17**, 104–111.

Zhang, K. & Liao, X., 2004. A new asymptotic method for the analysis of convection in a rapidly rotating sphere, *Journal of Fluid Mechanics*, **518**, 319–346.

