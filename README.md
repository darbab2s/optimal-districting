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
```math
\begin{flalign}
\text{Minimiere } &\sum_{i \in V} \sum_{j \in V} d_{ij} x_{ij}^2 \\
&+ \lambda_1 * ( \sum_{j \in V} x_{j j} - p )^2 \\ 
&+ \lambda_2 * ( \sum_{j \in V} x_{ij} - 1 )^2 \\
&+ \lambda_3 * ( - \sum_{i \in V} w_{i}^{(a)} x_{ij} + (1-\tau^{(a)} ) \mu^{(a)} x_{j j} )^2 \\
&+ \lambda_4 * ( \sum_{i \in V} w_{i}^{(a)} x_{ij} - (1+\tau^{(a)}) \mu^{(a)} x_{j j}  )^2 \\
&+ \lambda_5 * ( x_{ij} - x_{ii}  )^2 \\
&x_{i j}  \in\{0,1\} &  i, j \in V
\end{flalign}
```

Expanded and Ordered:
```math
\begin{flalign}
\text{Minimiere } &\sum_{i \in V} \sum_{j \in V} d_{ij} x_{ij} \\
&+ \lambda_1 * \bigg( \Big(\sum_{j \in V} x_{j j}^2 + 2\sum_{i < j} x_{i i} x_{j j} \Big)  - 2p \sum_{j \in V} x_{j j} + p^2 \bigg)\\ 
&+ \lambda_2 * \bigg( \Big( \sum_{j \in V} x_{ij}^2 + 2\sum_{k < j} x_{ij} x_{ik} \Big)  - 2\sum_{j \in V} x_{ij} + 1 \bigg) \\
&+ \lambda_3 * \bigg( \Big( \sum_{i \in V} w_{i}^2 x_{ij}^2  + 2\sum_{h < i} w_{i}w_{h} x_{ij} x_{hj} \Big)   - 2\mu (1 - \tau) x_{j j} \sum_{i \in V} w_{i} x_{ij} + (1 - \tau)^2 \mu^{{(a)}^2} x_{j j}^2 \bigg) \\
&+ \lambda_4 * \bigg( \Big( \sum_{i \in V} w_{i}^2 x_{ij}^2  + 2\sum_{h < i} w_{i}w_{h} x_{ij} x_{hj} \Big)   - 2\mu (1 + \tau) x_{j j} \sum_{i \in V} w_{i} x_{ij} + (1 + \tau)^2 \mu^{{(a)}^2} x_{j j}^2 \bigg) \\
&+ \lambda_5 * ( x_{ij}^2 + x_{ii}^2 -2x_{ii}x_{ij}   ) \\
&x_{i j}  \in\{0,1\} &  i, j \in V
\end{flalign}
```

QUBO:
