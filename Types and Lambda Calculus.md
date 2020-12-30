# Types and Lambda Calculus

### 1. Terms

*λ*x. *M* : 							**x** as var **M** as function

(*λ*x. *M*)*N* :	    				**N** as input

(*λ*x. *M*)*N* =$_{β}$ *M*[*N**/**x*]		subscript just saying its not identical	

$\mathcal{Λ}$									  terms	*alphabet* $\mathbb{V}$ + {*λ*, ., (, )}

##### definition 1.1 (Terms)

Three rules:

​								       	application					 abstraction rule

$x \in \mathbb{V} \;\frac{}{x \in \mathbb{Λ}} \quad\textrm{Var}$		$\frac{M \in \mathbb{Λ} \quad N \in \mathbb{Λ}}{(MN) \in \mathbb{Λ}} \quad\textrm{App}$		$x \in \mathbb{V} \; \frac{M \in \mathcal{Λ}}{(λx.M) \in \mathcal{Λ}} \quad\textrm{Abs}$

<p style="color:red">
1. A variable always follow a lambda<br>
2. No parentheses are allowed between lambda and the following dot<br>
3. A dot and a term must follow λx
</p>

A string *M* is a member of *Λ* iff there is a *proof tree* built from the rules (Var), (App) and (Abs) with conclusion *M* *∈* $\mathcal{Λ}$	.

**Syntactical conventions**:

•  Omit the outermost parentheses. MN => (*MN*). 

•  Assume that application **associates to the left**. MNP => ((MN)P)

•  Body of an abstraction extends as far to the right as possible.  

​	λx. MN => (λx.(MN))

•  Iterated abstractions can be grouped. 	λx y. M => (λx.(λy. M))



### 2. Alpha

##### definition 2.1

Free variables:

1. FV(x) = {x}

2. FV(*PQ*) = FV(*P*) ∪ FV(*Q*)
3. FV(*λx*.*N*) = FV(*N*) \ {x}

*A term* *M* *without free variables is said to be* **closed** *or a* **combinator**. The set of all closed terms is written Λ^0^.

 $FV(M)  \neq  \emptyset$ is said to be open

##### definition 2.2

Capture-avoiding substitution :

* ​       y[N/x] = N                             if x = y
* ​	   y[N/x] = y 						     if x $\neq$ y
* ​       (PQ)[N/x] = P[N/x]Q[N/x] 
* ​       (λy. P)[N/x] = λy. P               if *y* = *x* 
* ​       (λy. P)[N/x] = λy. P[N/x]      if *y*  $\neq$ *x* *and* *y* $\not\in$ FV(*N*)

##### definition 2.3

***α***-**equivalence**:

If two terms M and N can be made identical just by changing bound variable names to fresh names (not already used inside them), we say they are *α-equivalent*.

##### defifinition 2.4.

 The set of λ-terms is the set $\mathcal{Λ}$ with all α-equivalent terms identifified.



### 3. Beta

##### definition 3.1 

one-step $ \beta$

A term of the form (λx. M)N is called a β-redex and we say that M[N/x] is the contraction of the redex.	(reducible expression)

##### definition 3.2

**one-step** $\beta$-**reduction** written infix as $→_β$, defined by following:

​											$\frac{}{(λx.M)N →_β M[N/x]}(Redex)$

$\frac{M →_β M'}{MN →_β M'N}(AppL)$			$\frac{N →_β N'}{MN →_β MN'}(AppR)$				$\frac{M →_β N}{λx.M →_β λx.N}(Abs)$

If M $\to_\beta$ N then we say that N is a **reduct** of M. A term M is said to be in **β-normal form** just if there is no term N for which M $\to_\beta$  N.

If its “*β*-reduces” then it does so in a sequence of zero or more steps. Written as M $\twoheadrightarrow_β$ N

##### definition 3.3 ($\beta$-reduction)

$\beta$-reduction:

Whenever there is a possibly empty sequence of consecutive one-step reductions

$M \to_β M_1 \to_β  M_2 \to_β ... \to_\beta M_{k-1}\to_\beta M_k$

##### definition 3.4

nomenclature: 

- If  M $\twoheadrightarrow_β$ N then N is a **reduct** of M. If M $\ne_β$ N, then it is a **proper reduct** 
- Term M such that M $\twoheadrightarrow$ N for some normal form N is said to **have a normal form ** or be **normalisable**
- Term M for which there is no infinite reduction sequence $M \to_β M_1 \to_β  M_2 \to_β ...$ is said to be **strongly normalisable**

**I** $:=$ λx. x								   					**I**M $\twoheadrightarrow_\beta$ M

**K** $:=$  λxy. x 							   				   **K**MN $\twoheadrightarrow_\beta$ M

**S** $:=$  λxyz. xz(yz)				     					**S**MNP $\twoheadrightarrow_\beta$ MP(NP)

$\omega :=$ λx. xx													$\omega M \twoheadrightarrow_\beta MM$

$\Omega := \omega\omega$														$\Omega \twoheadrightarrow_\beta \Omega$

$\Theta :=$ (λxy. y(xxy))(λxy. y(xxy))					$\Theta M \twoheadrightarrow_\beta M(\Theta M)$

$Y = \lambda f.(\lambda x.f(xx))(\lambda x.f(xx))$			$M(YM) =_\beta YM$

**I** is called identity combinator

$\Theta$ sometimes called Turing's combinator

**Confluence of $\beta$-reductionN**

##### theorem 3.1 (Confluence of $\beta $)   **

If $M \twoheadrightarrow_\beta P$ and $M \twoheadrightarrow_\beta Q$ then there exists a term N such that $P \twoheadrightarrow_\beta N$ and $Q \twoheadrightarrow_\beta N$

##### definition 3.5 ($\beta$-convertibility)

$\beta$-convertibility

M and N be terms, if M and N have a common reduct , then M and N are $\beta$-convertible and write $M =_\beta N$



### 4. Definability

##### definition 4.1

**Church numeral** for the number n, abbreviated $\ulcorner n \urcorner$, is:

![image-20201020180133085](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201020180133085.png)

$\ulcorner0 \urcorner=_\beta λfx.x$

$\ulcorner k+1 \urcorner=_\beta λfx.f(\ulcorner k \urcorner fx)$

##### definition 4.2 ($\lambda$-definability)

A function *f* : N *× ··· ×* N *→* N on k-tuples of natural numbers is said to be λ-**definable** just if there exists a λ-term F that satisfifies the equation:

​									$F\ulcorner n_1 \urcorner... \ulcorner n_k \urcorner =_\beta \ulcorner f(n_1,...,n_k)\urcorner$

**Add** $:=$ λyz.λfx.yf(zfx)									**Add**$\ulcorner m\urcorner \ulcorner n\urcorner=_\beta \ulcorner m+n \urcorner$

**Pred** $:=$ λz.λfx.z(λgh.h(gf))(λu.x)(λu.u)		**Pred**$\ulcorner 0  \urcorner =_\beta \ulcorner0 \urcorner$	**Pred**$\ulcorner n + 1 \urcorner =_\beta \ulcorner n\urcorner$

**Sub** $:=$ λmn.n **Pred** m		 					**Sub**$\ulcorner m \urcorner \ulcorner n\urcorner=_\beta \ulcorner 0\urcorner$ if m$\leq $ n

​																	**Sub**$\ulcorner m\urcorner \ulcorner  n\urcorner=_\beta \ulcorner m-n\urcorner $ otherwise

**IfZero** $:=$ λxyz.x(**K**z)y 		 					**IfZero**$\ulcorner 0 \urcorner \ulcorner  p\urcorner  \ulcorner q\urcorner =_\beta \ulcorner p\urcorner $

​											   					**IfZero** $\ulcorner n+1\urcorner  \ulcorner p\urcorner \ulcorner q \urcorner =_\beta \ulcorner q\urcorner $

**mult** $:=$ λnmf.n(mf).



##### definition 4.3 (Church Lists)

**Church encoding** of a list xs is the term $\ulcorner xs \urcorner $ define recursively by:

​								$\ulcorner [\;] \urcorner = λcn.n$

​								$\ulcorner n:ns \urcorner = λcn.c\ulcorner n\urcorner(\ulcorner ns \urcorner cn)$

Nil$:=$ λcn.n			Cons $:=$ λxy.λcn.cx(ycn)		Sum$:=$ λxs.xs **Add** $\ulcorner 0 \urcorner$



### 5. Recursion

##### definition 5.1

We defifine fact as the unique function on natural numbers (i.e. subset of N *×* N with the property that exactly one output number is associated with each input number) that satisfifies the equation (in parameter F):

​									F(n) = if n = 0 then 1 else n · F(n - 1)

##### definition 5.2

A λ-term N is said to be a **fixed point** of another λ-term M just if MN $=_\beta$ N

##### theorem 5.1 (First Recursion Theorem) **

Every λ-term posesses a fixed point 

Y-combinator:	$\lambda f.(\lambda x.f(xx))(\lambda x.f(xx))$

$M(YM) =_\beta YM$

### 6. Induction

The induction principle for $\mathcal{Λ}$

Let $\Phi$ be some property of $\lambda$-terms, if the following all met:

(LI1)	For all variables x, $\Phi$ holds of x.

(LI2)	For all terms P and Q, if $\Phi$ holds of P and $\Phi$ holds of Q then $\Phi$ holds of PQ

(LI3)	For all terms P and variables x, if $\Phi$ holds of P then $\Phi$ holds of $\lambda x.P$

Then it follows that $\Phi$ holds of all $\lambda$-terms

##### lemma 6.1

For all $\lambda$-terms M, for all $\lambda$-terms N: if x $\notin$ FV(M) then FV(M[N/x]) = FV(M)



Induction Principles:

Let $\Phi$ be a property of natural numbes, If all of the following conditions are met:

(NI1)	$\Phi$ holds of 0

(NI2)	For all n $\in \mathbb{N}$, if $\Phi$ holds of n then $\Phi$ holds of n+1

Then it follows that, for all natural numbers n $\in \mathbb{N}$, $\Phi$ holds of n

​					$(Zero) \frac{}{0 \in \mathbb{N}}$ 							$(Succ)\frac{n\in \mathbb{N}}{n+1 \in \mathbb{N}}$

![image-20201022141036540](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201022141036540.png)

![image-20201022141331403](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201022141331403.png)

### 7. Types

##### definition 7.1

We assume a countable set of **type variables** $\mathbb{A}$, ranged over by a,b,c and other lowercase letters from the start of the alphabet. The **monotypes**, written $\mathbb{T}$ are a set of strings defined inductively by the following rules:

$(TyVar)  a\in \mathbb{A}\frac{}{a \in \mathbb{T}}$ 										$(Arrow)\frac{A\in \mathbb{T} \; B\in \mathbb{T}}{(A\to B) \in \mathbb{T}}$

• We omit the outermost parenthesis when writing types.

• We assume that the arrow **associates to the right**: i.e. when we write $A_1$ *→* $A_2$ → $A_3$ , the type that we mean is ($T_1$ → ($A_2 \to A_3$))

The **type schemes** are pairs consisting of a finite set of type variables *a*1 , . . . , $a_m$ and a monotype A, that we write suggestively as:

​											$\forall a_1 ...a_m.A$

parentheses example:

$a\to b\to b	 = (a\to (b \to b))$

$(a\to a)\to b = ((a\to a) \to b)$

$\forall ab.a \to a \to b = \forall ab.(a\to (a \to b))$

##### definition 7.2

set of a type(schema) $\forall \overline{a}.A$ written $FTV(\forall\; \overline{a}.A)$, recursively on the syntax:

$FTV(a) = \{a\}$

$FTV(A\to B) = FTV(A)\cup FTV(B)$

$FTV(\forall a_1...a_m.A) = FTV(A) \backslash \{a_1,...,a_m\}$

##### definition 7.3

A **type substitution** is a total map $\sigma : A \to \mathbb{T}$ from type variables to monotypes, with the propeprty that $\sigma(a) \neq a $ only for finitely many $a\in \mathbb{A}$

We will use σ, τ and θ to stand for type substitutions generically.

##### definition 7.4

Given monotype A and a type substitution $\sigma$, we write $A\sigma$ for the monotype which is defined recursively as follows:

$a\sigma = \sigma(a)$

$(A_1 \to A_2)\sigma = A_1\sigma \to A_2\sigma$

for example:

![image-20201025224351008](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201025224351008.png)

![image-20201025224339161](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201025224339161.png)

##### definition 7.5

We write $\sigma_1\sigma_2$ for the substitution obtained by composing $\sigma_2$ after $\sigma_1$

$(\sigma_1\sigma_2)(a) := (\sigma_1(a))\sigma_2$

$A(\sigma_1\sigma_2) = (A\sigma_1)\sigma_2$



### 8. System

##### definition 8.1

A **type assignment** is a pair of a term M and a type A, written M : A. The term part of a type assignment is called the subject and the type part the predicate.

##### definition 8.2

A **type environment**, generically written as $\Gamma$, is a finite set of type assignments of the form $x:\forall \overline{a}.A$ which is. moreover, consisitent, in the sense that if $x :\forall \overline{a}.A \in \Gamma$ and  $x :\forall \overline{a}.B \in \Gamma$ then  $\forall \overline{a}.A = \forall \overline{a}.B$.

The subsects of $\Gamma$ is the set, written dom $\Gamma$, of those term variables x for which there is some $\forall \overline{a}.A$ such that $x :\forall \overline{a}.A \in \Gamma$.

we extend type substitution to type environment, defining:

$\Gamma \sigma = \{x:S\sigma | x: S \in \Gamma\}$

##### definition 8.3 (Type System)

A **type judgement** is a triple consisting of a type environment $\Gamma$, a $\lambda$-term M and a monotype A, which we write:

$\Gamma \vdash M : A$

The type system rule:

$x:\forall \overline{a}.A \in \Gamma \frac{}{\Gamma \vdash x:A[ \overline{B}/\overline{a}]}(TVar)$

$\frac{\Gamma \vdash M : B\to A \; \Gamma \vdash N : B}{\Gamma \vdash MN:A}(TApp)$

$x \notin dom \;\Gamma\; \frac{\Gamma \cup \{x:B\} \vdash M:A}{\Gamma \vdash \lambda x.M: B \to A}(TAbs)$

In type theory, a proof tree justifying a type judgement is usually called a **type derivation**

##### definition 8.4

We say that a closed term **M** is **typeable** just if some type A such that $\vdash M:A$ is derivable in the system.

##### lemma 8.1

The term $\lambda x.xx$ is untypable.

##### theorem 8.1 (Inversion)	**

Suppose $\Gamma \vdash M :A$ (is derivable), then:

- If M is a variable x, then there is a type scheme $\forall \overline{a}.B$ (with $\\overline{a}$ possibly enpty) and A = B[$\overline{C}/\overline{a}$] for some monotypes $\overline{C}$
- If M is an application PQ, then there is a type B such that $\Gamma \vdash P : B \to A$ and $\Gamma \vdash Q:B$
- If M is an abstraction $\lambda x.P$, then there are types B and C such that A = B $\to$ C, and $\Gamma$, $x:B\vdash P:C$



### 9. Analysis

##### lemma 9.1 **

Suppose M is a term, $\Gamma$ an environment ans A a type. Then:

**(Subterm Closure)**	If $\Gamma \vdash M:A$ is derivable and N is a subterm of M then there is some $\Gamma' \supseteq \Gamma$ and some $A'$ such that $\Gamma' \vdash N:A'$.

**(Relevance-1)**	If $\Gamma \vdash M:A$, then $FV(M) \subseteq dom(\Gamma)$

**(Relevance-2)**	If $\Gamma \vdash M:A$, then $\{ x: \forall \overline{b}.B| x:\forall \overline{b}.B \in \Gamma \and x \in FV(M)\} \vdash M:A$

**(Weakening)** 	If $\Gamma \vdash M:A$ and $\Gamma \sube \Gamma'$ then $\Gamma' \vdash M:A$

##### theorem 9.1 (Subject Reduction) **

If $\Gamma \vdash M:A$ and $M \to_\beta N$ then $\Gamma \vdash N:A$

##### lemma 9.2

If $\Gamma$, $x:B\vdash M:A$ and $\Gamma \vdash N:B$ then $\Gamma \vdash M[N/x]:A$

##### theorem 9.2 (The Subformula Property) **

Suppose $\Gamma$ assigns only monotypes to its subjects and suppose M is in $\beta$-normal form and $\Gamma \vdash M:A$. Then the derivation of this judgement is unique and all of the types mentioned in the derivation are substring of the types mentioned in the conclusion.



### 10. Constraints

##### definition 10.1

A **type constraint** is just a pair of menotypes (A,B) written suggestively as $A \stackrel{?}{=} B$

Hindley-Milner Type Inference

1.  Constraint generation
2.  Constraint solving

CGen$(\Gamma,x)$= 

​		let a be fresh

​		let $\forall a_1 ... a_k.A = \Gamma(x)$

​		let $b_1,..., b_k$ be fresh

​		$(a,\{a \stackrel{?}{=}A[b_1/a_1,...,b_k/a_k]\})$

CGen$(\Gamma,MN)$= 

​		let a be fresh

​		let $(b,C_1) = CGen(\Gamma, M)$

​		let $(b,C_2) = CGen(\Gamma, N)$

​		$(a, C_1 \cup C_2 \{b \stackrel{?}{=} c\to a\})$

CGen$(\Gamma,\lambda x.M)$= 

​		let a be fresh

​		let b be fresh

​		let $(c,C) = CGen(\Gamma \cup \{ x:b\}, M)$

​		$(a, C \cup \{a \stackrel{?}{=} b\to c\})$

![image-20201111213843332](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201111213843332.png)



### 11. Unification

##### definition 11.1

A **unifier** or **solution** to a finite set of type constraints $\{A_1 \stackrel{?}{=} B_1,..., A_n \stackrel{?}{=} B_n\}$ is a type substitution $\sigma$ such that, for all $1 \le i \le n, A_i\sigma = B_i\sigma$

$\mathscr{C}\sigma$ for the application of $\sigma$ to all types involved in $\mathscr{C}$

##### lemma 11.1 (CGen: Recursive Invariant)

Suppose CGen($\Gamma$,M) = $(a,\mathscr{C})$

​	If $\sigma$ is a unifier for $\mathscr{C}$ then $\Gamma \sigma \vdash M : \sigma(a)$ is a derivable typing judgement.

​	If $\Gamma \sigma \vdash M : \sigma(a)$ is a derivable typing judgement, then $\sigma$ is a unifier of $\mathscr{C}$.

In particulat, when $\Gamma$ is empty because M is close, this says that $\sigma$ is a unifier of $\mathscr{C}$ iff $\vdash M:\sigma(a)$

##### definition 11.2

A set of type constraints of the shape $\mathscr{C} = \{a_1 \stackrel{?}{=} A_1,... a_m \stackrel{?}{=}  A_m \}$ is in **solved form** just if each of the $a_i$ are pairwise distinct variable none of which occurs in any of the $A_i$.

In such a case, we define $[\![ \mathscr{C} ]\!] := [A_1/a_1,...,A_m/a_m]$.

##### definition 11.3

Suppose $\mathscr{C}$ is a set of type constraints. The **unification algorithm** consiss of a applying the following rules to $\mathscr{C}$ as many times as possible.

(1)	$\{ A \stackrel{?}{=} A \} \uplus \mathscr{C} \Longrightarrow \mathscr{C}$

(2)	$\{ A_1 \to A_2 \stackrel{?}{=} B_1 \to B_2 \} \uplus \mathscr{C} \Longrightarrow \{A_1 \stackrel{?}{=} B_1,  A_2 \stackrel{?}{=} B_2\}\mathscr{C}$

(3) 	$\{ A \stackrel{?}{=} a \} \uplus \mathscr{C} \Longrightarrow  \{ a \stackrel{?}{=} A \}\mathscr{C}$										$if\; A \notin \mathbb{A}$

(4)	$\{ a \stackrel{?}{=} A \} \uplus \mathscr{C} \Longrightarrow  \{ a \stackrel{?}{=} A \}\uplus\mathscr{C}[A/a]$		$if \; a \in FTV(\mathscr{C})\setminus FTV(A)$

$\uplus$ mean disjoint union. It's two arguments must have no element in common.

##### theorem 11.1

Suppose $\mathscr{C}$ is a set of type constraints and $\mathscr{D}$ is the problem obtained from it by the unification algorithm. Then $\mathscr{C}$ is solvable iff $\mathscr{D}$  is in solved form.

##### defintion 11.4

Let $\mathscr{C}$ e a set of type constraints. Then we say that $\sigma$ is a **most general unifier(mgu)** of $\mathscr{C}$ just if:

(i)	$\sigma$ is a unifier of $\mathscr{C}$

(ii)   and every unifier $\sigma'$ of $\mathscr{C}$ is of shape $\sigma \sigma''$ for some $\sigma''$

##### theorem 11.2

If $\mathscr{C}$ is solvable and $\mathscr{D}$ is the problem obtained by running the unification algorithm, then $[\![ \mathscr{C} ]\!]$ is an mgu

##### corollary 11.1

Every solvable set of type constraints has a most general solution

##### definition 11.5

Hindley-Milner Type Inference Algorithm

On input closed term M:

1. Generate contraints $\mathscr{C}$ and type variable a using CGEN($\emptyset, M$)
2. Solve $\mathscr{C}$ using Robison's algorithm to obtain mgu $\sigma$ or deduce unsolveability
3. If $\mathscr{C}$ has no solution then M is untypeable. Otherwise return $\sigma(a)$

##### theorem 11.3 (Principal Type Scheme Theorem)  **

If colsed term M is typable, then Hindley-Milner type inference returns a type A that is **principal** in the sense that:

​		$\vdash M:A$ is derivable

​		and, if some other $\vdash M:B$ is deriable, then there is a choice of monotypes $C_1,...,C_k$ such that  $B = A[C_1/a_1,...C_k/a_k] $



### 12. Normalisation

##### definition 12.1

Define $R : \mathbb{T} \to \mathscr{P}(\Lambda)$ is a function from types to sets of terms defined recurively as follows.

$R(a) = \{M | M \; is \;SN\}$

$R(A\to B) = \{M|\forall N \in R(A).MN\in R(B)\}$

$R(\forall \overline{a}.A) = \{M | for \; all \; \overline{B} \in \mathscr{P}(\mathbb{T}), M \in R(A[\overline{B}/\overline{a}]) \}$



variable-headed strongly normalising:

$VHSN := \{ xN_1 ... N_k| x\in \mathbb{V} \and k \geq 0 \and \forall i \in [1..k].N_i \in Sn\}$

##### lemma 12.1

for all $A:VHSN \sube R(A) \sube SN$

for all A:

(i)	for all $M:M \in VHSN$ implies $M\in R(A)$

(ii)   for all $M:M \in R(A)$ implies $M$ is $SN$

##### lemma 12.2

if, for all $N\in R(B):M[N/x] \in R(A)$, then for all $N:(\lambda x.M)N \in R(B_m)$

##### theorem 12.1

suppose $\Gamma \vdash M:B$ and, fo reach variable $x \in dom(\Gamma)$, there is a term $N_x$ such that $N_x \in R(\Gamma(x))$. Then $M[N_x/x|x\in dom(\Gamma)] \in R(B)$

##### Corollary 12.1 (Strong Normalisation)	**

If $\Gamma \vdash M:A$ then $M$ is $SN$.

### 13. Curry-Howard

##### definition 13.1

The **inhabitation problem**, is the problem of, given a type A, determining if there a closed term M such that $\vdash M:A$

##### lemma 13.1

Types $a \to b$ (with $a \ne b$) and $(a\to b)\to b$ are not inhabited

##### lemma 13.3

Formulas $(a\Rightarrow a \Rightarrow b)\Rightarrow a \Rightarrow b$ and $((a \Rightarrow a) \Rightarrow b) \Rightarrow b$ are vaild

##### theorem 13.1 (Curry-Howard)		**

If we consider properly labelled proofs in the implicational fragment of propositional logic (i.e. the only connective is implication), then the following is true:

​	From a constructive of A from starting assumptions $\Gamma$, one can extract a term M such that $\Gamma \vdash M:A$

​	From each term $M$ such that $\Gamma \vdash M:A$, we can extract a constructive proof that A follows from assumptions $\Gamma$.





### Prove

We can conclude everything from false





### Revision mistake

**Week one :** outer parentheses and in subterms application associates to the left.