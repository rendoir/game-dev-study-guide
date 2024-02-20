# Math

## Algebra
### Cross product
- Formula: $\vec{a} \times \vec{b} = |\vec{a}| \cdot |\vec{b}| \cdot sin(\theta)$
- Anticommutativity: $\vec{a} \times \vec{b} = -\vec{b} \times \vec{a}$
- Distributivity: $\vec{a} \times (\vec{b} + \vec{c}) = \vec{a} \times \vec{b} + \vec{a} \times \vec{c}$
- Scalar Multiplication Property
- Is 0 when theta is 0º or 180º, positive for ]0,180[ and negative for ]180,360[

### Dot product
- Formula: $\vec{a} \cdot \vec{b} = |\vec{a}| \cdot |\vec{b}| \cdot cos(\theta)$
- Commutative, Distributive, Scalar Multiplication Property
- Is 0 when perpendicular

### Planes
- Vectorial formula: $\vec{X} = \vec{P} + s \cdot \vec{a} + t \cdot \vec{b}$
- Cartesian formula: $\vec{n_x} \cdot x + \vec{n_y} \cdot y + \vec{n_z} \cdot z = k$

### Lines
- Vectorial formula: $\vec{X} = \vec{P} + t \cdot \vec{a}$
- Cartesian formula: $y = m \cdot x + b$

### Matrices
- $A^{-1} \times A = A \times A^{-1} = I$
- Inverse obtained through Gauss-Jordan: Start with $A$ on the left side and $I$ on the right. Linearly combine the rows to achieve $I$ on the left and $A^{-1}$ on the right.
- Orthogonal if $A^{-1} = A^T$

### Change of basis
- Nomenclature
    - Basis: N-dimensional basis are defined by at least N linearly independent vectors
    - Orthogonal Basis: all basis vectors are perpendicular (dot product is zero)
    - Orthonormal Basis: orthogonal basis where all basis vectors have unit length
- Change of basis matrix: $M_{u \rightarrow e}$
- $E \times X_e = U \times X_u$
- $X_e = M_{u \rightarrow e} \times X_u$
- $M_{u \rightarrow e} = E^{-1} \times U$
- $M_{u \rightarrow e} = M_{e \rightarrow u}^{-1}$
- If E and U are orthonormal basis, then E and U are orthogonal matrices:
    - $M_{u \rightarrow e} = E^{T} \times U$
    - $M_{u \rightarrow e} = M_{e \rightarrow u}^{T}$
- Basis to matrix: One column is a vector of the basis

### Quaternions
- Multiplication (3D rotation along an axis)  
    - Axis: $\vec{v} = (v_1, v_2, v_3)$
    - Point: $P = (x, y, z)$
    - $Q = a + bi + cj + dk$
    - $Q^{-1} = a - bi - cj - dk$
    - $P = xi + yj + zk$
    - $P' = Q \times P \times Q^{-1}$
    - $a = \cos \frac{\theta}{2}$
    - $b = v_1 \sin \frac{\theta}{2}$
    - $c = v_2 \sin \frac{\theta}{2}$
    - $d = v_3 \sin \frac{\theta}{2}$

### Ray-Sphere Intersection
- Sphere: $(P - C) \cdot (P - C) = r^2$
- Ray: $A + t\vec{B}$
- $(A+t\vec{B}-C) \cdot (A+t\vec{B}-C) = r^2$
- $\equiv (A-C) \cdot (A-C) + 2t (A-C) \cdot \vec{B} + t^2 \vec{B} \cdot \vec{B} = r^2$
- Solve with the quadratic equation
    - If $b^2-4ac<0$ : Missed
    - If $b^2-4ac=0$ : Tangent ($t_0=t_1$)
    - If $b^2-4ac>0$ : Intersected
        - If both t are positive, the ray is facing the sphere.
        - If one t is positive and one t is negative, the ray is shooting from the inside.
        - If both t are negative, the ray is shooting away from the sphere, and technically ray-sphere intersection is actually impossible.

## Physics
### Uniformly accelerated movements
- $v(t) = v_i + a \cdot (t-t_i)$
- $x(t) = x_i + v_i \cdot (t-t_i) + \frac{a}{2} \cdot (t-t_i)^2$
- $v(x)^2 = v_i^2 + 2a \cdot (x-x_i)$
