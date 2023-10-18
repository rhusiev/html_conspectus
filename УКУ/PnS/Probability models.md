# Probability axioms
- $P(A) \geq 0$
- $P(\Omega) = 1$
- $\forall A_1, A_2, ...$ - mutually exclusive events: $P(\bigcup A_j) = \sum P(A_j)$


# Probability space
*Probability space* = $\displaystyle \l\{\Omega, \mathscr{F}, P\r\}$

$\Omega$ - *sample space*

$\mathscr{F}$ - *family of events*: (usually all possible) sets of elementary events
For example for $\Omega=\l\{1, 2, 3\r\}$:
$\mathscr{F}=\l\{\{\varnothing\}, \{1\}, \{2\}, \{3\}, \{1, 2\}, \{1, 3\}, \{2, 3\}, \{1, 2, 3\}\r\}$
An element of $\mathscr{F}$ is called an *event*.

$P$ - *probability* for each element of $\mathscr{F}$


$\mathscr{F}$ must be a *$\sigma$-field*:
- $\Omega \in \mathscr{F}$
- $A \in \mathscr{F} \Rightarrow \overline{A} \in \mathscr{F}$
- $A_1, A_2, ..., A_n, ... \in \mathscr{F} \Rightarrow \bigcup A_j \in \mathscr{F}$

This also means that:
- $\varnothing \in \mathscr{F}$
- $A, B \in \mathscr{F} \Rightarrow A \cap B \in \mathscr{F}; A \cup B \in \mathscr{F}; A \\ B \in \mathscr{F}$


# Terms
$A^c = \overline{A} = A' = \Omega \backslash A$
*sum* - $A \cup B$
*product* - $A \cap B$
*implication* - $A \subset B$
*mutual exclusion* - $A \cap B = \varnothing$
*disjoint* - the same, $A \cap B = \varnothing$
probability of *A, given* that *B* happened - $\displaystyle P(A \mid B) = \frac{P(A \cap B)}{P(B)}$

*Independent events* - $P(A \cap B) = P(A) \cdot P(B) \Leftrightarrow P(A \mid B) = P(A)$
==| It only makes sense if they can occur at the same time, so if $A \cap B = \varnothing$ - they are not independent(unless one of them has probability 0) |==


