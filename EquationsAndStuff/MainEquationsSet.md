[Go back to README](README.md)
</br>
VBEMWS uses Maxwell Equations
We start with 4 equations:

<details>

<summary>Faradays law of induction</summary>

**Assume it's in vacuum**\
$$\nabla \times {\vec {E}}=-{\frac {\partial {\vec {B}}}{\partial t}}$$
</details>

<details>

<summary>Ampère-Maxwell equation</summary>

**Assume it's in vacuum**\
$$\nabla \times {\vec {B}}=\mu _{0}\varepsilon _{0}{\frac {\partial {\vec {E}}}{\partial t}}$$
</details>

<details>

<summary>Gauss equations</summary>

**Assume it's in vacuum**\
$$\nabla \cdot {\vec {E}}=0$$
</br>
$$\nabla \cdot {\vec {B}}=0$$
</details>

Next you use **vector identity** $$\nabla \times (\nabla \times \mathbf{A}) = \nabla (\nabla \cdot \mathbf{A}) - \nabla^2 \mathbf{A}
$$
</br>
which gives us two equations(one for E and one for B):
</br>
$$\nabla^2 {\vec {B}} = \mu _{0}\varepsilon _{0}{\frac {\partial^2 {\vec {B}}}{\partial^2 t}}$$
</br>
$$\nabla^2 {\vec {E}} = \mu _{0}\varepsilon _{0}{\frac {\partial^2 {\vec {E}}}{\partial^2 t}}$$

