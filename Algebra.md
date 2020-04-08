### Cross product
- a * b = |a| * |b| * sin(theta)
- Anticommutativity: a * b = -b * a 
- Distributivity: a * (b + c) = a * b + a * c
- Scalar Multiplication Property
- Is 0 when theta is 0º or 180º, positive for ]0,180[ and negative for ]180,360[

### Dot product
- a . b = |a| * |b| * cos(theta)
- Commutative, Distributive, Scalar Multiplication Property
- Is 0 when perpendicular

### Planes
- Vectorial formula:  
X = P + s * a + t * b  
- Cartesian formula:  
n.x * x + n.y * y + n.z * z = k

### Line
- Vectorial formula:  
X = P + t * a
- Cartesian formula:  
y = m * x + b

### Matrices
- A^(-1) * A = A * A^(-1) = I
- Inverse obtained through Gauss-Jordan: Start with A on the left side and I on the right. Linearly combine the rows to achieve I on the left and A^(-1) on the right.
- Orthogonal if A^(-1) = A^T

### Change of basis
- Change of basis matrix M_u->e
- Xe = M_u->e * Xu
- E * Xe = U * Xu
- M_u->e = E^(-1) * U
- M_u->e = (M_e->u)^(-1)
- If E and U are orthonormal basis, then E and U are orthogonal matrices:
    - M_u->e = E^T * U
    - M_e->u = (M_u->e)^T
- Basis to matrix: One column is a vector of the basis
