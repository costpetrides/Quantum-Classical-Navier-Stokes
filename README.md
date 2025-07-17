#  Quantum-Classical Navier–Stokes Solver

###  Classical Model

This solver implements the 2D incompressible Navier–Stokes equations using the SIMPLE algorithm on a staggered finite volume grid:

$$
\begin{aligned}
\text{Momentum:} \quad & \rho \left( \frac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla \mathbf{u} \right) = -\nabla p + \mu \nabla^2 \mathbf{u} \\
\text{Continuity:} \quad & \nabla \cdot \mathbf{u} = 0
\end{aligned}
$$

Pressure correction is applied iteratively to enforce mass conservation.

---

###  Hybrid Classical–Quantum Model

This variant integrates a hybrid classical–quantum approach within the pressure correction step of the SIMPLE algorithm.

#### Governing Equations

$$
\begin{aligned}
\text{Momentum:} $\quad & \rho \left( \frac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla \mathbf{u} \right) = -\nabla p + \mu \nabla^2 \mathbf{u}$ \\
\text{Continuity:} $\quad & \nabla \cdot \mathbf{u} = 0$
\end{aligned}
$$

#### Algorithm Highlights

- **Discretization:** Finite volume method (staggered grid).
- **Velocity prediction:** Solves momentum equations for intermediate velocities $ \( \mathbf{u}^*, \mathbf{v}^* \)$.
- **Pressure correction:** Solves the Poisson equation \( \nabla^2 p' = \nabla \cdot \mathbf{u}^* \) for pressure update $\( p = p^* + \alpha_p p' \)$.
- **Quantum patch:** A central 3×3 subdomain of the Poisson equation is solved via `quantum_poisson_solver()` (VQE-compatible placeholder).
- **Boundary conditions:** Lid-driven cavity flow (top wall moving, others stationary).

