# Tensor Network

## Matrix

A matrix has two indices. Consider a $3 \times 4$ matrix $A$. It has $3$ rows and $4$ columns. The entry in the $i$-th row and $j$-th column is denoted as $A_{i,j}$ or $A[i,j]$. The first index represents the row index, while the second index represents the column index. It is commonly written in box brackets.

$$
[A] =
\left[ \begin{array}{cccc}
  A_{0,0} & A_{0, 1} & A_{0,2} & A_{0,3} \\
  A_{1,0} & A_{1, 1} & A_{1,2} & A_{1,3} \\
  A_{2,0} & A_{2, 1} & A_{2,2} & A_{2,3}  
\end{array} \right]
$$

A matrix of size $1 \times D$ represents a row vector

$$
[A] =
\left[ \begin{array}{cccc}
  A_{0,0} & A_{0, 1} & A_{0,2} & A_{0,3}
\end{array} \right]
$$

A matrix of size $D \times 1$ represents a column vector.

$$
[A] =
\left[ \begin{array}{c}
  A_{0,0} \\
  A_{1,0} \\
  A_{2,0}   
\end{array} \right]
$$

When we use index notation,
* The index before the comma "," is the row-index.
* The index after the comma "," is the column-index.
* The size $D_1 \times D_2$ is the shape $(D_1, D_2)$ of the matrix.

## Rank-N tensor or N-dimensional array
A rank-N tensor or N-dimensional array $A$ has $N$ indices. The entry is denoted as

$$
  A_{i_1 i_2 i_3 \cdots i_N}.
$$
Its shape $(D_1, D_2, \cdots, D_N)$ determine the range of the index $i_j$, i.e., $ 0 \le i_j < D_j$.

In order to map naturally a rank-N tensor to a matrix we put a comma "," among the indices. A rank-N tensor with $N_c$ row indices is denoted as

$$
  A_{i_1 i_2 i_3 \cdots i_{N_c}, i_{N_c+1}, \cdots i_N}.
$$

Note that the $j$-th shape $D_j$ can be 1 and $i_j=0$ is a constant.

For example,
* A rank-2 tensor with shape (1, D) represents a row vector, with entries $A_{0,i}$.
* A rank-2 tensor with shape (D, 1) represents a column vector.

### Combined index

We can combined several (subsequent) indices into a single combined index. Consider three indices $ijk$ with shape $(D_i, D_j, D_k)$. We can combine (reshape) them into a single index $\alpha$ with shape $D_\alpha=D_i*D_j*D_k$. The process is denoted as $(ijk) \rightarrow \beta$. Equivalently we can simply use $(ijk)$ to represents a **combined-index**.

We use the following convention: For $(D_i, D_j, D_k)=(2,2,2)$ so that $D_\beta=8$, one has
* $ (0,0,0) \rightarrow 0$
* $ (0,0,1) \rightarrow 1$
* $ (0,1,0) \rightarrow 2$
* $ (0,1,1) \rightarrow 3$
* $ (1,0,0) \rightarrow 4$
* $ (1,0,0) \rightarrow 5$
* $ (1,1,0) \rightarrow 6$
* $ (1,1,1) \rightarrow 7$

## Graphical representation

We represent a rank-2 tensor $A_{i,j}$ as
````
  ┏━━━╳━━━┓
i─┨   A   ┠─j
  ┗━━━━━━━┛
````
We put the name of the tensor at the centor of the box. If we want to specific the shape information, we can put them inside the box near the bond.
````
  ┏━━━━╳━━━━┓
i─┨Di  A  Dj┠─j
  ┗━━━━━━━━━┛
````


The `╳` on top is to break the rotational symmetry. So that even if we rotate the figure, it still uniquely represents the same tensor and will not be confused with its transpose.
````
  ┏━━━╳━━━┓       ┏━━━━━━━┓
i─┨   A   ┠─j = j─┨   A   ┠─i
  ┗━━━━━━━┛       ┗━━━╳━━━┛
````

When a line connects two tensors, it implies a summation. So the following figure corresponds to $\sum_j A_{i,j} B_{j,k}$, which is nothing but the matrix multiplication $[A][B]$.
````
  ┏━━━╳━━━┓     ┏━━━╳━━━┓
i─┨   A   ┠──j──┨   B   ┠─j
  ┗━━━━━━━┛     ┗━━━━━━━┛
````

Actually, we can remove the dummy index and represent $[C]=[A][B]$ as
````
  ┏━━━╳━━━┓     ┏━━━╳━━━┓  ┏━━━╳━━━┓
 ─┨   C   ┠─ = ─┨   A   ┠──┨   B   ┠─
  ┗━━━━━━━┛     ┗━━━━━━━┛  ┗━━━━━━━┛
````


## Tensor Network Notation

Introduction to tensor Network
````
#                       0
#                 ┌─────┘
#                 │ ┏━━━╳━━━┓
#                 └─┨d MT0 d┠─┐
#                   ┗━━━━━━━┛ │                                    0
#                 ┌────100────┘                              ┌─────┘
#                 │ ┏━━━╳━━━┓                                │ ┏━━━╳━━━━┓
#    ┏━━━╳━━━┓    └─┨d      ┃      ┏━━━╳━━━┓                 └─┨d       ┃
# 1──┨d MT1 d┠─101──┨d  T  d┠──102─┨d  M2 d┠──2    =     1 ────┨d TOUT d┠──── 2
#    ┗━━━━━━━┛      ┃      d┠─┐    ┗━━━━━━━┛                   ┃       d┠─┐
#                   ┗━━━━━━━┛ │                                ┗━━━━━━━━┛ │
#                 ┌────103────┘                                    ┌──────┘              
#                 │ ┏━━━╳━━━┓                                      3
#                 └─┨d  M3 d┠─┐
#                   ┗━━━━━━━┛ │
#                       ┌─────┘
#                       3

````
