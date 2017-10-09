# Exercises
## Exercise 1

$n$ saliors pick a room between $1\dots n$, independently. What is the probability that no sailor returns to his own cabin? Prove that this probability is $\frac{1}{e}$.

**PROVE:** $P($ no sailor returns to his own cabin $)$ = $\frac{1}{e}$.

**CORRECTION:**

We have then the event $e_i$ that the sailor $i$ fails choosing his cabin. $P(e_i) = 1-\frac{1}{n}$.

Probability that they all fail $P(\bigcap_{i=1}^n e_i) = (1-\frac{1}{n})^n = \frac{1}{e}$.

## Exercise 2

Suppose you are given a biased coin for which $p = P($ HEAD $)$ is *unknown*. How can you use it for generating *unbiased* flips? Give a scheme for which the expected number of flips of the biased coin for extracting one unbiased flip is $\frac{1}{p(1-p)}$.

**CORRECTION:**

We have to consider 2 consecutive flips, then we have 4 possible outcomes: $HH, TT, HT, TH$. We can have then the probabilities for each outcome:

| outcome | probability |
|-|-|
|$HH$ |$p^2$|
|$TT$ |$(1-p)^2$|
|$HT$ |$p(1-p)$|
|$TH$ |$p(1-p)$|

Then $P(TH) = P(HT)$, we can then say that $TH$ represents the tail and $HT$ represents the head, as they have the same probability to be gotten, so it's unbiased.

$$P(TH \cup HT)=2p(1-p)$$

$$E(\mathbb{\#repetitions})= \frac{1}{2p(1-p)}$$

$$E(\mathbb{\#flips})= 2 \frac{1}{2p(1-p)} = \frac{1}{p(1-p)}$$

## Exercise 3

a) How many executions of a Monte-Carlo Algorithm $A$ are required to raise its success probability from $1 - \epsilon_1$ to $1 - \epsilon_2$ ? $(0 < \epsilon_2 < \epsilon_1 < 1)$.

**CORRECTION:**

Probability that at least one succeeds: $P(\mathbb{success}) = 1 - \epsilon^t$. We wish then $1-\epsilon^t \geq 1 - \epsilon_2$.

$$1-\epsilon^t \geq 1 - \epsilon_2 \Leftrightarrow \epsilon_1^t \leq \epsilon_2$$

$$t\ln \frac{1}{\epsilon_1} \geq \ln \frac{1}{\epsilon_2}$$

$$t \geq \frac{\ln \frac{1}{\epsilon_2}}{\ln\frac{1}{\epsilon_1}}$$



b) Prove that we can go from the case where *the probability of success is polynomially small* to a case where *the probability of error is exponentially small* by only changing the degree of the polynomial bounding the running time.

**CORRECTION:**

// to finish
