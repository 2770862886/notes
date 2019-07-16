% Algorithms
<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

Introduction of Algorithms
==========================

Analysis of Algorithm
---------------------

The analysis of algorithm is the theoretical study of computer program performance  
and resource usage.  

What's more important than performance?

### Problem: Sorting ###

Input: sequence $<a_1, a_2, a_3, ... a_n>$ of
Output: 


$$ y = x_i^{a_1^2} $$
$$ y = x^2 \; \mbox{(二次函数)} $$

### Insertion sort ###

+ Insertion.Sort(A, n) // sorts A[1...n]

$$ T(n) = \sum_{j=2}^\infty\theta(j) = \theta(n^2) $$

``` pseudo

```

+ Running time
1) Depends on input size (e.g. already sorted)
2) 


+ BIG IDEA! Asymptotic analysis
1) Ignore machine dependent runing time.
2) Look at growth of  $T(n) n \to \infty$

+ Asymptotic notation
$\theta$ notation: Drop low order terms
                   Ignore leading constants  

Ex: $3n^3 + 90n^2 = \theta(n^3)$

### Merge Sort ###

Merge Sort $A[1...n]$
1. If n = 1, done.
2. Recursively sort:
   A[1...n/2] and  
   A[n/2+1...n]  
3. Merge 2 sorted list  

Key subroutine: merge

$$ T(n)= \begin{cases} \theta(1) & \text {(n=1)} \\ 2T(n/2) + \theta(n) & \text {(n>1)} \end{cases} $$

Recursion tree: $T(n)=2T(n/2) + cn$
