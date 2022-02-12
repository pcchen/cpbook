# Ising Model

## Ising model in one dimension

The Hamiltonian is

$$
  E[\{s\}, N] = -J \sum_{i=1}^N s_i s_{i+1} - h \sum_{i=1}^N s_i.
$$
where $s_i=\pm 1$ and $s_{i+N}=s_i$.

The ordinary partition function is

$$
  Z[N, \beta] = \sum_{s} e^{-\beta E[\{s\}, N]}
$$

Let's write it out.

$$
  Z = \sum_{s}
  e^{\beta h s_1} e^{\beta J s_1 s_2}
  e^{\beta h s_2} e^{\beta J s_2 s_3}
  e^{\beta h s_3} e^{\beta J s_3 s_4}
  e^{\beta h s_4} e^{\beta J s_4 s_5}
$$

$$
  Z = \sum_{s_1} \sum_{s_2} \sum_{s_3} \sum_{s_4}
  \left( e^{\beta h s_1/2} e^{\beta J s_1 s_2} e^{\beta h s_2/2} \right)
  \left( e^{\beta h s_2/2} e^{\beta J s_2 s_3} e^{\beta h s_3/2} \right)
  \left( e^{\beta h s_3/2} e^{\beta J s_3 s_4} e^{\beta h s_4/2} \right)
  \left( e^{\beta h s_4/2} e^{\beta J s_4 s_5} e^{\beta h s_1/2} \right)
$$

Define a $2\times 2$ *transfer matrix* $T$, with elements
$ T_{s, s^\prime} = e^{\beta h s_i/2} e^{\beta J s_i s_j} e^{\beta h s_j/2} $.

$$
  [T] = \left[\begin{array}{cc}
    e^{\beta J} e^{\beta h} & e^{-\beta J} \\
    e^{-\beta J} & e^{\beta J} e^{\beta h}
  \end{array}\right].
$$

Then

$$
  Z
  = \sum_{s_1} \sum_{s_2} \sum_{s_3} \sum_{s_4}
  T_{s_1, s_2} T_{s_2, s_3} T_{s_3, s_4} T_{s_4, s_1}
  = \text{Tr}\left( T^4 \right).
$$

We have $Z[N]=\text{Tr}\left( T^N \right)$.

## Ising model in two dimensions

## Ising model in three dimensions
