# Math

## Algebra
### Cross product
- Formula: <img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\times&space;\vec{b}&space;=&space;|\vec{a}|&space;\cdot&space;|\vec{b}|&space;\cdot&space;sin(\theta)"/>
- Anticommutativity: <img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\times&space;\vec{b}&space;=&space;-\vec{b}&space;\times&space;\vec{a}"/>
- Distributivity: <img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\times&space;(\vec{b}&space;&plus;&space;\vec{c})&space;=&space;\vec{a}&space;\times&space;\vec{b}&space;&plus;&space;\vec{a}&space;\times&space;\vec{c}"/>
- Scalar Multiplication Property
- Is 0 when theta is 0º or 180º, positive for ]0,180[ and negative for ]180,360[

### Dot product
- Formula: <img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\cdot&space;\vec{b}&space;=&space;|\vec{a}|&space;\cdot&space;|\vec{b}|&space;\cdot&space;cos(\theta)"/>
- Commutative, Distributive, Scalar Multiplication Property
- Is 0 when perpendicular

### Planes
- Vectorial formula: <img src="https://latex.codecogs.com/svg.latex?\vec{X}&space;=&space;\vec{P}&space;&plus;&space;s&space;\cdot&space;\vec{a}&space;&plus;&space;t&space;\cdot&space;\vec{b}"/>
- Cartesian formula: <img src="https://latex.codecogs.com/svg.latex?\vec{n_x}&space;\cdot&space;x&space;&plus;&space;\vec{n_y}&space;\cdot&space;y&space;&plus;&space;\vec{n_z}&space;\cdot&space;z&space;=&space;k"/>

### Lines
- Vectorial formula: <img src="https://latex.codecogs.com/svg.latex?\vec{X}&space;=&space;\vec{P}&space;&plus;&space;t&space;\cdot&space;\vec{a}"/>
- Cartesian formula: <img src="https://latex.codecogs.com/svg.latex?y&space;=&space;m&space;\cdot&space;x&space;&plus;&space;b"/>

### Matrices
- <img src="https://latex.codecogs.com/svg.latex?A^{-1}&space;\times&space;A&space;=&space;A&space;\times&space;A^{-1}&space;=&space;I"/>
- Inverse obtained through Gauss-Jordan: Start with A on the left side and I on the right. Linearly combine the rows to achieve I on the left and <img src="https://latex.codecogs.com/svg.latex?A^{-1}"/> on the right.
- Orthogonal if <img src="https://latex.codecogs.com/svg.latex?A^{-1}&space;=&space;A^T"/>

### Change of basis
- Nomenclature
    - Basis: N-dimensional basis are defined by at least N linearly independent vectors
    - Orthogonal Basis: all basis vectors are perpendicular (dot product is zero)
    - Orthonormal Basis: orthogonal basis where all basis vectors have unit length
- Change of basis matrix <img src="https://latex.codecogs.com/svg.latex?M_{u&space;\rightarrow&space;e}"/>
- <img src="https://latex.codecogs.com/svg.latex?X_e&space;=&space;M_{u&space;\rightarrow&space;e}&space;\times&space;X_u"/>
- <img src="https://latex.codecogs.com/svg.latex?E&space;\times&space;X_e&space;=&space;U&space;\times&space;X_u"/>
- <img src="https://latex.codecogs.com/svg.latex?M_{u&space;\rightarrow&space;e}&space;=&space;E^{-1}&space;\times&space;U"/>
- <img src="https://latex.codecogs.com/svg.latex?M_{u&space;\rightarrow&space;e}&space;=&space;M_{e&space;\rightarrow&space;u}^{-1}"/>
- If E and U are orthonormal basis, then E and U are orthogonal matrices:
    - <img src="https://latex.codecogs.com/svg.latex?M_{u&space;\rightarrow&space;e}&space;=&space;E^{T}&space;\times&space;U"/>
    - <img src="https://latex.codecogs.com/svg.latex?M_{u&space;\rightarrow&space;e}&space;=&space;M_{e&space;\rightarrow&space;u}^{T}"/>
- Basis to matrix: One column is a vector of the basis

### Quaternions
- Multiplication (3D rotation along an axis)  
    - Axis: <img src="https://latex.codecogs.com/svg.latex?\vec{v}&space;=&space;(v_1,&space;v_2,&space;v_3)"/>
    - Point: <img src="https://latex.codecogs.com/svg.latex?P&space;=&space;(x,&space;y,&space;z)"/>
    - <img src="https://latex.codecogs.com/svg.latex?Q&space;=&space;a&space;&plus;&space;bi&space;&plus;&space;cj&space;&plus;&space;dk" />
    - <img src="https://latex.codecogs.com/svg.latex?Q^{-1}&space;=&space;a&space;-&space;bi&space;-&space;cj&space;-&space;dk"/>
    - <img src="https://latex.codecogs.com/svg.latex?P&space;=&space;xi&space;&plus;&space;yj&space;&plus;&space;zk"/>
    - <img src="https://latex.codecogs.com/svg.latex?P'&space;=&space;Q&space;\times&space;P&space;\times&space;Q^{-1}"/>
    - <img src="https://latex.codecogs.com/svg.latex?a&space;=&space;\cos&space;\frac{\theta}{2}"/>
    - <img src="https://latex.codecogs.com/svg.latex?b&space;=&space;v_1&space;\sin&space;\frac{\theta}{2}"/>
    - <img src="https://latex.codecogs.com/svg.latex?c&space;=&space;v_2&space;\sin&space;\frac{\theta}{2}"/>
    - <img src="https://latex.codecogs.com/svg.latex?d&space;=&space;v_3&space;\sin&space;\frac{\theta}{2}"/>

### Ray-Sphere Intersection
- Sphere: <img src="https://latex.codecogs.com/svg.latex?(P&space;-&space;C)&space;\cdot&space;(P&space;-&space;C)&space;=&space;r^2"/>
- Ray: <img src="https://latex.codecogs.com/svg.latex?A&space;&plus;&space;t\vec{B}"/>
- <img src="https://latex.codecogs.com/svg.latex?(A&plus;t\vec{B}-C)&space;\cdot&space;(A&plus;t\vec{B}-C)&space;=&space;r^2"/>
- <img src="https://latex.codecogs.com/svg.latex?\equiv&space;(A-C)&space;\cdot&space;(A-C)&space;&plus;&space;2t&space;(A-C)&space;\cdot&space;\vec{B}&space;&plus;&space;t^2&space;\vec{B}&space;\cdot&space;\vec{B}&space;=&space;r^2"/>
- Solve with the quadratic equation
    - If <img src="https://latex.codecogs.com/svg.latex?b^2-4ac<0"/> : Missed
    - If <img src="https://latex.codecogs.com/svg.latex?b^2-4ac=0"/> : Tangent (<img src="https://latex.codecogs.com/svg.latex?t_0=t_1"/>)
    - If <img src="https://latex.codecogs.com/svg.latex?b^2-4ac>0"/> : Intersected
        - If both t are positive, the ray is facing the sphere.
        - If one t is positive and one t is negative, the ray is shooting from the inside.
        - If both t are negative, the ray is shooting away from the sphere, and technically ray-sphere intersection is actually impossible.

## Physics
### Uniformly accelerated movements
- <img src="https://latex.codecogs.com/svg.latex?v(t)&space;=&space;v_i&space;&plus;&space;a&space;\cdot&space;(t-t_i)"/>
- <img src="https://latex.codecogs.com/svg.latex?x(t)&space;=&space;x_i&space;&plus;&space;v_i&space;\cdot&space;(t-t_i)&space;&plus;&space;\frac{a}{2}&space;\cdot&space;(t-t_i)^2"/>
- <img src="https://latex.codecogs.com/svg.latex?v(x)^2&space;=&space;v_i^2&space;&plus;&space;2a&space;\cdot&space;(x-x_i)"/>