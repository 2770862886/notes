% Algorithms

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Sqrt](https://www.cnblogs.com/huashanqingzhu/p/6635691.html)
[Newton](http://sofasofa.io/forum_main_post.php?postid=1000182)
[Data Community](http://sofasofa.io/index.php)

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

Asymptotic Notation
-------------------

### $O$ notation ###


### $\Omega$ notation ###


### $\theta$ notation ###




Recursion-tree method
---------------------

Master method
-------------




-------------------------------------------------------------------------------

| no | name    | phonetic    | capital | lower |
|----|:--------|-------------|---------|-------|
| 1  | alpha   | /'ælfə/     | Α       | α     |
| 2  | beta    | /'beɪtə/    | Β       | β     |
| 3  | gamma   | /'gæmə/     | Γ       | γ     |
| 4  | delta   | /'deltə/    | Δ       | δ     |
| 5  | epsilon | /'epsɪlɒn/  | Ε       | ε     |
| 6  | zeta    | /'zi:tə/    | Ζ       | ζ     |
| 7  | eta     | /'i:tə/     | Η       | η     |
| 8  | theta   | /'θi:tə/    | Θ       | θ     |
| 9  | iota    | /aɪ'əʊtə/   | Ι       | ι ℩   |
| 10 | kappa   | /'kæpə/     | Κ       | κ     |
| 11 | lambda  | /'læmdə/    | Λ       | λ     |
| 12 | mu      | /mju:/      | Μ       | μ     |
| 13 | nu      | /nju:/      | Ν       | ν     |
| 14 | xi      | /ˈksaɪ/     | Ξ       | ξ     |
| 15 | omicron | /ˈɑmɪˌkrɑn/ | Ο       | ο     |
| 16 | pi      | /paɪ/       | Π       | π     |
| 17 | rho     | /rəʊ/       | Ρ       | ρ     |
| 18 | sigma   | /'sɪɡmə/    | Σ       | σ ς   |
| 19 | tau     | /taʊ/       | Τ       | τ     |
| 20 | upsilon | /ˈipsilon/  | Υ       | υ     |
| 21 | phi     | /faɪ/       | Φ       | φ     |
| 22 | chi     | /kaɪ/       | Χ       | χ     |
| 23 | psi     | /psaɪ/      | Ψ       | ψ     |
| 24 | omega   | /oʊ'meɡə/   | Ω       | ω     |

* Αα alpha常用作形容词，以显示某件事物中最重要或最初的。
* Ββ beta也能表示电脑软件的测试版，通常指的是公开测试版，提供一般使用者协助测试并回报问题。
* Ι ι ℩ 有时用来表示微细的差别。
* Δ 在初中数学里也表示一元二次方程的判别式，事实上，不少希腊字母被用在数学和物理上。
* Ο ο Omicron(国际音标/'ɑmɪ,krɑn/)字面上的意思是“小的 O”（ὄμικρόν），以便与“大 O”（ω“ὦμέγα）区别。
* Σ σ ς 在希腊语中，如果一个单词的最末一个字母是小写σ，要把该字母写成 ς。
* Ψ ψ 意为神秘的、未知的。
* Ω ω 用作指事情的终结，对应指开始的alpha。
