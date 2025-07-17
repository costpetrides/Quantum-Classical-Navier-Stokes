# Quantum-Classical-Navier-Stokes

###  Classical Model

This solver implements the 2D incompressible Navier–Stokes equations using the SIMPLE algorithm on a staggered finite volume grid:

$$
\begin{aligned}
\textbf{Momentum:} \quad & \rho \left( \frac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla \mathbf{u} \right) = -\nabla p + \mu \nabla^2 \mathbf{u} \\
\textbf{Continuity:} \quad & \nabla \cdot \mathbf{u} = 0
\end{aligned}
$$

Pressure correction is used to enforce mass conservation iteratively.
