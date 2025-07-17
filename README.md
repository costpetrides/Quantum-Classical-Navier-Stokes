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


### Hybrid  Classical - Quantum Model

This code solves the 2D incompressible Navier–Stokes equations using the SIMPLE algorithm on a staggered finite volume grid. It optionally uses a **hybrid classical–quantum approach** for pressure correction within a subdomain.

#### Governing Equations

$$
\begin{aligned}
& \text{Momentum:} \quad \rho \left( \frac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla \mathbf{u} \right) = -\nabla p + \mu \nabla^2 \mathbf{u} \\
& \text{Continuity:} \quad \nabla \cdot \mathbf{u} = 0
\end{aligned}
$$

#### Algorithm Highlights

- **Discretization:** Finite volume method (staggered grid).
- **Velocity prediction:** Solves momentum equations for intermediate velocities \( \mathbf{u}^*, \mathbf{v}^* \).
- **Pressure correction:** Solves Poisson equation \( \nabla^2 p' = \nabla \cdot \mathbf{u}^* \) for pressure update \( p = p^* + \alpha_p p' \).
- **Hybrid solver:** A small pressure sub-block is solved via a placeholder `quantum_poisson_solver()` to simulate a future quantum-assisted solution (e.g. via VQE).
- **Boundary conditions:** Lid-driven cavity flow.

```

---

Let me know if you’d like an additional figure or equation image included automatically (as a badge or PNG).
