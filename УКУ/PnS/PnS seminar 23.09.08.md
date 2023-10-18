# Seminar 1: Basic notions of probability

## Problem 1

> A standard card deck contains 52 cards of four different suits (hearts ♡, diamonds ♢, clubs ♣, and spades ♠) of values 2 to 10 and face cards (jacks, queens, kings, and aces). Assign the ranks 1 to 13 to each of these cards (rank 13 to aces, rank 12 to kings and so on). Arman is dealt 5 random cards from the deck; let R be the highest rank among his cards. We want to calculate the probability of the event that R = 10

Let $A$ be a set of all cards

Sample space: $\l\{ (n_1, n_2, n_3, n_4, n_5) \mid (n_1, n_2, n_3, n_4, n_5) \in A^5, \text{all } n_i \text{ are different} \r\}$

Elementary events: every such $(n_1, n_2, n_3, n_4, n_5)$

a) It is basically a random choice of five different cards, so there is no difference in the order of cards. As the probability of choosing a card is the same for every card, we can use the classical probability here

b) The probability that $\l\{R \le k\r\} \Leftrightarrow$ the probability that all 5 cards are $\le k$. Let it be the event $A_k$

$\displaystyle P(A_k) = \frac{C_{4k}^5}{C_{52}^5}$

c) Let the probability that $R = 10$ be $P(A)$. It is
$\displaystyle P(A_{10}) - P(A_9) = \frac{C_{4 \cdot 10}^5}{C_{52}^5} - \frac{C_{4 \cdot 9}^5}{C_{52}^5} = \frac{C_{40}^5 - C_{36}^5}{C_{52}^5} = \frac{658008 - 376992}{2598960} \approx 0.108$

d) Directly:

$$
\begin{flalign}
    & P(A) = \frac
    {C_4^1 \cdot C_{36}^4 + C_4^2 \cdot C_{36}^3 + C_4^3 \cdot C_{36}^2 + C_4^4 \cdot C_{36}^1}
    {C_{52}^5} = &\\
    & = \frac
    {4 \cdot 58905 + 6 \cdot 7140 + 4 \cdot 630 + 1 \cdot 36}
    {2598960} \approx 0.108&
\end{flalign}
$$

Our answers in c) and d) are the same

## Problem 2

> Anna, Ben, Charlie, and Diane along with other 8 students are randomly seated in the same row of the lecture hall

a) $\displaystyle \frac{\cm{Count Ben and Anna as one}{P_{11}} \cdot 2}{P_{12}}$

b) Let `B` - next to Charlie, `C` - next to Diane
$\displaystyle 1 - P(B) - P(C) + P(C \cap B) = 1 - \frac{P_{11} \cdot 2}{P_{12}} \cdot 2 + \frac{P_{10} \cdot 2}{P_{12}}$

c) $\displaystyle \cm{Being next to Ben}{\frac{P_{11} \cdot 2}{P_{12}}} - \underbrace{2 \cdot \frac{P_{10} \cdot 2}{P_{12}}}_{\text{Being next to Ben and (Charlie or Diane)}}$

d) If in a circle(Let's fix Anna):
    a) $\displaystyle \frac{P_{10} \cdot 2}{P_{11}}$
    b) $\displaystyle 1 - 2 \cdot \frac{P_{10} \cdot 2}{P_{11}} + \frac{P_9 \cdot 2}{P_{11}}$
    c) $\displaystyle \frac{P_{10} \cdot 2}{P_{11}} - \cm{Next to Ben and (Charlie or Diane)}{\frac{P_9 \cdot 2}{P_{11}} \cdot 2}$

## Problem 3

> Alice, Bob, Chris, and Diane are playing the poker card game. From a standard deck of 52 cards, each player is dealt 5 cards

a) $\displaystyle \frac{\overbrace{C_{48}^{16}}^{\text{All, except aces}}}{C_{52}^{20}}$

b) $\displaystyle \frac{\cm{All except aces}{A_{48}^{16}} \cdot \cm{aces}{P_{4}}}{A_{52}^{20}}$

c) $\displaystyle \frac{(\cm{For each ace}{4} \cdot \cm{All other not aces}{C_{48}^{4}} \cdot P_5) \cdot A_{47}^{15}}{A_{52}^{20}}$

d) $\displaystyle \frac{4 \cdot C_{48}^{4}}{C_{52}^{5}} + \frac{C_{4}^{2} \cdot C_{48}^3}{C_{52}^5} + \frac{C_4^3 \cdot C_{48}^2}{C_{52}^5} + \frac{48}{C_{52}^5}$

e) $\displaystyle \frac{4 \cdot 3 \cdot A_{50}^{18}}{A_{52}^{20}}$

f) $\displaystyle \frac{P_4 \cdot A_{48}^{16}}{A_{52}^{20}}$

## Problem 4

> In a standard M&M’s bag, the candies come in 6 different colours. Alice chooses 10 candies at random. How many different combinations can she get?

a) $\displaystyle \overline{C}\._{6}^{10} = C_{15}^{10}$ - If we just consider combinations, not the sequence

b) Sample space - all possible combinations of 10 candies

Elementary events - every such combination

Assumption: the probability of choosing a candy is the same for every candy, doesn't change when we take a candy

$\displaystyle c_1 + c_2 + c_3 + c_4 + c_5 + c_6 = 10,$ $\forall i: c_i \ge 1$
$\displaystyle c_1' + c_2' + c_3' + c_4' + c_5' + c_6' = 4$
So the probability: $\displaystyle \frac{\overline{C}\._{6}^4}{\overline{C}\._6^{10}} = \frac{C_9^4}{C_{15}^{10}}$

c) $\displaystyle C_{24}^9 \cdot C_{15}^8$

d) $\displaystyle \frac{\overbrace{C_{22}^8 \cdot C_{15}^8}^\text{if Alice in the first team} + C_{16}^9 C_{22}^7 + C_{22}^6 \cdot C_{17}^8}{C_{24}^9 \cdot C_{15}^8}$

## Problem 5

> Arman generates two random numbers x and y from the interval \[0, 1\] using the random() function in Python

We assume that Python gives a random number from the interval \[0, 1\] with a uniform distribution and with infinite precision(which means that we have an interval from 0 to 1)

The sample space is $\l\{(x, y) \mid x, y \in [0, 1]\r\}$, which forms a square with a side of length 1

Thus, we can use the geometric probability here

a) ![[PnS seminar 23.09.08 problem 5.a]]

Probability: $\displaystyle \frac{3}{4}$

b) ![[PnS seminar 23.09.08 problem 5.b]]

Probability: $\displaystyle \frac{1}{2}$

c) $\displaystyle \frac{x + y}{2} \in [0, 0.5]$
$\displaystyle 0 \le x + y \le 1$

![[PnS seminar 23.09.08 problem 5.c]]

Probability: $\displaystyle \frac{1}{2}$

d) $\displaystyle 1 - x \le | x - y |$
$$
\begin{flalign}
    & 1 - x \le x - y \Leftrightarrow y \le 2x - 1 \text{ or} &\\
    & 1 - x \le y - x \Leftrightarrow y \ge 1 &\\
\end{flalign}
$$
![[PnS seminar 23.09.08 problem 5.d]]

Probability: $\displaystyle \frac{1}{4}$

e) Intervals of lengths $x$, $y$, and $1$ form an acute-angled triangle.

$x \le 1$ and $y \le 1$ $\Rightarrow$ The angles between ($x$ and $1$) and ($y$ and $1$) are always acute

Therefore we have to only make sure that the angle between $x$ and $y$ is acute

Using the cosine theorem: $\displaystyle 1^2 = x^2 + y^2 - 2xy \cdot \cos \alpha$
$$
\begin{flalign}
    & \cos \alpha = \frac{x^2 + y^2 - 1}{2xy} \ge 0 \cm{x and y are $\ge$ 0}{\Leftrightarrow}&\\
    & x^2 + y^2 \ge 1&\\
\end{flalign}
$$

![[PnS seminar 23.09.08 problem 5.e]]

Probability: $\displaystyle \frac{2^2 - \pi \cdot 1^2}{4 \cdot 1^2} = \frac{4 - \pi}{4}$
