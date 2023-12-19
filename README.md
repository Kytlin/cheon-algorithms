NOTE: Program is still in working progress as "Cheon-BSGS.ipynb"

<h1>Project Overview</h1>

A SageMath implementation based on Izu's et al. paper for Baby-step-Giant-step (BSGS) and Pollard's Kangaroo (Lambda) algorithm apllied on a generalized ECDLP, namely, DLP with auxiliary inputs (DLPwAI). 


<h3> What does this program do? </h3>

The program solves cases where for an elliptic curve of on a general field $GF(p)$, where $p$ is a prime, $p-1$ has certain small divisors $d'$. Small divisor reduces the search space for powers of a primitive root $\zeta \in (\Z/r\Z)^*$, making this algorithm to run quickly for a 64-bit number $p$.

<h3> Why SageMath? </h3>

SageMath is a computer algebra software that has built-in elliptic curve operations.


<h3> Challenges </h3>

The main challenge is that the pseudocode presented in Izu's et al. paper does not provide a step-by-step procedure; one should understand the underlying elliptic curve attacks before applying the steps provided there, in which I was aided by the handbook.

Q: How does one define a pseudorandom function (`prf`)?

A: At first glance, I presumed the `prf` to be cryptographically secure function. I later found out that it could simple, with the only requirement that it should not reveal any properties of the group object.

Q: How is $a$ computed in the random walk function in the paper?

This is part was unclear until when I decided to carefully worked through the math within Section 19.6.1 of the handbook. I found out the $a$ corresponds to the distance travelled by the kangaroos.


Q: How to compute the hash pairs for BSGS?

A: We note that $\zeta^{r-1}G = G$ i.e. the order of $\zeta$ is $r-1$, so we are searching integers $u, v$ such that
$$\alpha^d\zeta^{r-u-1}=\zeta^{vd$}$

which will generate the same "baby-step" list as $\{G, \zeta^{-1} G, \ldots, \zeta^{-s} G\}$.

<h3> Reference </h3>

Cohen H., Frey G., et al. (2006). <i>Handbook of Ellipti and Hyperelliptic Curve Cryptography</i>. Chapman \& Hall/CRC.

Izu T., Takenaka M., \& Yasuda M. (2011). Experimental Analysis of Cheon's Algorithm against Pairing-friendly Curves. <i> Journal of Information Processing, Vol. 19</i>, 441-450. https://www.jstage.jst.go.jp/article/ipsjjip/19/0/19_0_441/_pdf