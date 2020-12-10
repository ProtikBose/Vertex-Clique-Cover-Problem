**Clique Cover Decision Problem :**

Given a graph G(V, E) and a number K, we need to answer yes or no if we can partition V(G) in K cliques

**Minimum Clique Cover Problem :**

Given a graph G(V, E), we need to output the smallest number for which clique cover exists. This number is called the clique cover number.

### Dataset
* 10 Randomly generated graphs
* DIMACS ( Center for Discrete Mathematics and Theoretical Computer Science)
* Implementation challenge for NP-hard problems (1993)
* 21 graphs with different edge density,nodes and edges 

[Here](https://mat.tepper.cmu.edu/COLOR04/clq.html) is the link of the dataset.

### Implementation

**Brute Force**

Naive algorithm, trying all the possible combinations of cliques.

**Backtracking**

Improvement of the Brute Force algorithm, that is able to stop its exploration of the solution if it is sure that there won't be any viable & better solution with the given configuration. The number of configurations tested is way smaller. Is quicker.

**Exact Algorithm**

Here the algorithm used is - "Sum Over Subset DP". The algorithm is - 

1) Find all Cliques.
2) For each subset S of N vertices count the number of clique which are subset of this subset using SOS dp.
3) Calculate the number of K size subset of all clique set  with repetition which misses at least one vertice.
4) If the above number of less than (total_clique)k, the we can cover the graph with k clique.

**Greedy Solution**

```
Input: graph G = [V, E]
permutation P = [P1, P2, ..., Pn] of vertices in V
Output: clique covering S of G

Algorithm:
for c = 1..n
sizes(c) = 0
for i = 1..n
    j = Pi
    c = find_equal(Γ(vj , c), sizes(c))
    Vc = Vc ∪ {vj}
return S = {V1, V2, ..., Vk}
```

**Iterated Greedy Solution**

```
Input: graph G = [V, E]
Output: clique covering S of G

Algorithm:
P = random permutation(1, 2, ..., n)
while stopping criterion is not met
    {V1, V2, ..., Vk} = GCC(G, P)
    with prev probability
        P = [Vk, Vk−1, ..., V1]
    else
        P = random permutation(V1, V2, ..., Vk)
    if ϑ(G) is known and k = ϑ(G)
        return S = {V1, V2, ..., Vk}
return S = {V1, V2, ..., Vk}
```
[Here](https://hull-repository.worktribe.com/output/438341) is the paper link for greedy and iterated greedy solution.
