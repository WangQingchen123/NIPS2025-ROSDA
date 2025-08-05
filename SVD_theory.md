1. **Separability and Spectral Rank**
Let the feature matrix of unknown samples be $\boldsymbol{Z}\in \mathbb{R}^{N \times d}$. If there are $k$ unknown classes and features are approximately linearly separable, the row space decomposes into $k$ nearly orthogonal subspaces. The spectral rank $rank_{\epsilon_T}(\mathbf{Z}) \triangleq \min\{r : \sum\_{i>r} \sigma_i^2 \le \epsilon_T \sum\_{i\ge 1} \sigma_i^2\}$ equals the number of dominant directions (Eckart–Young–Mirsky theorem), with $\epsilon_T=0.15$ (85% energy) offering robustness to noise [2–4].

3. **Spectral Properties of Cosine-Similarity Matrix**
For $\boldsymbol{M}=\boldsymbol{Z}\boldsymbol{Z}^\top$, under high intra-class similarity and low inter-class similarity:
- within-class variance ≪ between-class distance (class centers nearly orthogonal)
- noise energy ≤ between-class energy
$\boldsymbol{M} = \sum_{i=1}^{k} \lambda_i u_i u_i^\top + E,\quad \quad \|E\|_2 \le \delta$
where $N_c$ and $\sigma_c^2$ are the sample count and within-class energy of class $c$, respectively, and $\delta$ bounds the noise. The first $k$ eigenvalues $\lambda_i$ are well separated from the remainder, creating a spectral gap. Thus, the number of dominant eigenvalues equals the number of unknown classes $k$.

3. **Connection to Graph-Cut Theory: A Spectral-Clustering View.**
Regard $\boldsymbol{M}$ as the weighted adjacency matrix of a graph. The subspace spanned by the top $k$ eigenvectors of $\boldsymbol{M}$ is equivalent to the solution space of the normalized cut [5]. Also, a sharp drop between the $k$-th and $(k+1)$-th eigenvalue is sufficient for spectral clustering to recover the true number of clusters[6].

A response combining numerical and geometric insights is provided at [here](https://anonymous.4open.science/r/NIPS2025-ROSDA-7F77/shiyitu.pdf).

4. **Theoretical Guarantee.**
Based on the above analysis, we summarize a new lemma as follows:
> **Lemma**: Consider a similarity matrix $M\in\mathbb{R}^{n\times n}$ formed by samples from $k$ disjoint classes.
> - Ideal case.
If intra-class similarity is constant and inter-class similarity is zero, $M$ is block-diagonal:
![formula](https://quicklatex.com/cache3/a2/ql_0a4c07b60eb5b2963793c84cd8a72fa2_l3.png)
with $a_c \in (0,1]$. Each block is rank‑1, so the total rank is $k$; the top $k$ singular values are non-zero and correspond to the $k$ classes.
> - Noisy Case.
If $M=M_0+E$, where $M_0$ is the ideal block-diagonal matrix above and $\|E\|_2\leq\delta$, then by Weyl’s inequality [7]
$|\sigma_i(M)-\sigma_i(M_0)| \le\delta,\forall i$

so the top $k$ singular values remain separated, reliably indicating the true class number even under perturbations.

