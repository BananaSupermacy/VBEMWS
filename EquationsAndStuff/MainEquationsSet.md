[Go back to README](../README.md)
</br>
VBEMWS uses Maxwell Equations
We start with 4 equations:

<details>

<summary>Faradays law of induction</summary>

**General form (valid in vacuum and materials)**\
$$\nabla \times {\vec {E}}=-{\frac {\partial {\vec {B}}}{\partial t}}$$
</details>

<details>

<summary>Ampère-Maxwell equation</summary>

**General form (includes material response)**\
$$\nabla \times {\vec {H}}=\frac {\partial {\vec {D}}}{\partial t} + \vec{J}$$
</details>

<details>

<summary>Gauss equations</summary>

**Assuming no free charge in the domain**\
$$\nabla \cdot {\vec {D}}=0$$
</br>
$$\nabla \cdot {\vec {B}}=0$$
</details>

---

### Material relations

Since the simulation contains vacuum background and embedded objects with different physical properties, we introduce spatially dependent material parameters:

$$\vec{D} = \varepsilon(\mathbf{r}) \vec{E}$$
</br>
$$\vec{B} = \mu(\mathbf{r}) \vec{H}$$
</br>
$$\vec{J} = \sigma(\mathbf{r}) \vec{E}$$

Where:

- $\varepsilon(\mathbf{r})$ – permittivity (piecewise constant)
- $\mu(\mathbf{r})$ – permeability (piecewise constant)
- $\sigma(\mathbf{r})$ – conductivity (optional)

In vacuum:

$$\varepsilon = \varepsilon_0$$  
$$\mu = \mu_0$$  
$$\sigma = 0$$

Each object in the simulation has constant material parameters inside its volume.

---

### Substituting material relations into Maxwell equations

From Faraday:

$$\nabla \times \vec{E} = -\mu(\mathbf{r}) \frac{\partial \vec{H}}{\partial t}$$

From Ampère-Maxwell:

$$\nabla \times \vec{H} =
\varepsilon(\mathbf{r}) \frac{\partial \vec{E}}{\partial t}
+
\sigma(\mathbf{r}) \vec{E}$$

These two coupled first-order equations are the core equations used in the simulation.

---

### Important clarification

The following vector identity:

$$\nabla \times (\nabla \times \mathbf{A}) = \nabla (\nabla \cdot \mathbf{A}) - \nabla^2 \mathbf{A}$$

can be used to derive the classical wave equation **only in homogeneous vacuum**, where:

- $\varepsilon$ and $\mu$ are constants
- $\sigma = 0$

Under those strict conditions:

$$\nabla^2 {\vec {E}} = \mu_0\varepsilon_0{\frac {\partial^2 {\vec {E}}}{\partial t^2}}$$
</br>
$$\nabla^2 {\vec {B}} = \mu_0\varepsilon_0{\frac {\partial^2 {\vec {B}}}{\partial t^2}}$$

However, this form is **not valid** in the general simulation case because:

- $\varepsilon(\mathbf{r})$ and $\mu(\mathbf{r})$ vary spatially
- Discontinuities exist at object boundaries
- Conductive regions may exist

Therefore, the simulation solves the first-order Maxwell curl equations directly rather than the simplified Laplacian wave equation.

---

### Boundary modes

The simulation supports two boundary configurations:

**Mode 1 – Closed domain**

Physical boundary conditions may be imposed, such as:

- Perfect Electric Conductor (PEC): tangential $\vec{E} = 0$
- Perfect Magnetic Conductor (PMC): tangential $\vec{H} = 0$

---

**Mode 2 – Open domain**

To simulate wave propagation into free space:

- The computational domain is terminated with an absorbing boundary layer
- A Perfectly Matched Layer (PML) is used
- This prevents artificial reflections from numerical edges

Without an absorbing boundary, outgoing waves would reflect back into the domain.

