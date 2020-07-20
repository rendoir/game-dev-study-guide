### Cross product
- Formula:  
<img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\times&space;\vec{b}&space;=&space;|\vec{a}|&space;\cdot&space;|\vec{b}|&space;\cdot&space;sin(\theta)"/>
- Anticommutativity:  
<img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\times&space;\vec{b}&space;=&space;-\vec{b}&space;\times&space;\vec{a}"/>
- Distributivity:  
<img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\times&space;(\vec{b}&space;&plus;&space;\vec{c})&space;=&space;\vec{a}&space;\times&space;\vec{b}&space;&plus;&space;\vec{a}&space;\times&space;\vec{c}"/>
- Scalar Multiplication Property
- Is 0 when theta is 0º or 180º, positive for ]0,180[ and negative for ]180,360[

### Dot product
- Formula:  
<img src="https://latex.codecogs.com/svg.latex?\vec{a}&space;\cdot&space;\vec{b}&space;=&space;|\vec{a}|&space;\cdot&space;|\vec{b}|&space;\cdot&space;cos(\theta)"/>
- Commutative, Distributive, Scalar Multiplication Property
- Is 0 when perpendicular

### Planes
- Vectorial formula:  
<img src="https://latex.codecogs.com/svg.latex?\vec{X}&space;=&space;\vec{P}&space;&plus;&space;s&space;\cdot&space;\vec{a}&space;&plus;&space;t&space;\cdot&space;\vec{b}"/>
- Cartesian formula:  
<img src="https://latex.codecogs.com/svg.latex?\vec{n_x}&space;\cdot&space;x&space;&plus;&space;\vec{n_y}&space;\cdot&space;y&space;&plus;&space;\vec{n_z}&space;\cdot&space;z&space;=&space;k"/>

### Line
- Vectorial formula:  
<img src="https://latex.codecogs.com/svg.latex?\vec{X}&space;=&space;\vec{P}&space;&plus;&space;t&space;\cdot&space;\vec{a}"/>
- Cartesian formula:  
<img src="https://latex.codecogs.com/svg.latex?y&space;=&space;m&space;\cdot&space;x&space;&plus;&space;b"/>

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
