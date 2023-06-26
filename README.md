# optimal-districting

ConstrainedQuadratic Model:

```math
\begin{flalign}
\text{Minimiere} &\sum_{i \in V} \sum_{j \in V} d_{ij} x_{ij}^2  \nonumber \\
\text{u. d. N.} &\sum_{j \in V} x_{j j} = p  \\
&\sum_{j \in V} x_{ij} =1   & i \in V\\
&\sum_{i \in V} w_{i}^{(a)} x_{ij}  \geq \left(1-\tau^{(a)} \right) \mu^{(a)} x_{j j} & j \in V ; a \in A \\
&\sum_{i \in V} w_{i}^{(a)} x_{ij}  \leq \left(1+\tau^{(a)}\right) \mu^{(a)} x_{j j} & j \in V ; a \in A \\
&\sum_{i \in \cup_{v \in S}\left(N^{v} \backslash S \right)} x_{i j}-\sum_{i \in S} x_{i j}  \geq 1-|S| & j \in V ; S \subset\left[V \backslash\left(N^{j} \cup\{j\}\right)\right]\\
&x_{i j}  \in\{0,1\} &  i, j \in V
\end{flalign}
```

Lagrange Relaxation leads to:

QUBO:
```math
\begin{flalign}
\text{Minimiere } &\sum_{i \in V} \sum_{j \in V} d_{ij} x_{ij}^2 \\
&+ \lambda_1 * ( \sum_{j \in V} x_{j j} - p ) \\ 
&+ \lambda_2 * ( \sum_{j \in V} x_{ij} - 1 ) \\
&+ \lambda_3 * ( - \sum_{i \in V} w_{i}^{(a)} x_{ij} + (1-\tau^{(a)} ) \mu^{(a)} x_{j j} ) \\
&+ \lambda_4 * ( \sum_{i \in V} w_{i}^{(a)} x_{ij} - (1+\tau^{(a)}) \mu^{(a)} x_{j j}  ) \\
&+ \lambda_5 * ( x_{ij} - x_{ii}  ) \\
&x_{i j}  \in\{0,1\} &  i, j \in V
\end{flalign}
```
