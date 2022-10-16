# :chart_with_upwards_trend: Statistics: Fundamentals

Study Notes on `Fundamental Statistics`, `Probability`, `Distributions`, and `Regression`.

[Sagar Goswami: Github](https://github.com/GoswamiSagarD)


## DISCLAIMER
- This is a work in progress. I am still learning and I am not an expert in Statistics in any way. (I am just an Engineer interested in Statistics and other mysteries of the universe.)
- I am just trying to document my learning process. Feel free to comment and suggest changes. I am mainly referring to the following books:
    - `OpenIntro Statistics` by David M Diez, Christopher D Barr, Mine Çetinkaya-Rundel and OpenIntro Foundation.
    - `ISLR` by James, Witten, Hastie and Tibshirani.
- Github Copilot was used to create these notes.
    - There are some advantages of using Copilot, as it suggests entire equations related to the topic and specific to what I am writing. This makes it very quick and easy to work on the mathematical equations. I am literally in love with Copilot. It is a game changer. Documentation just got a lot easier. Fun fact: I am writing this disclaimer using Copilot. :smile:
    - However, there are some disadvantages as well, as it is not perfect and sometimes it does make wrong suggestions.
    - I have tried to correct as many mistakes as I could, but there might be some that I may have missed.
    - Also, it is very plausible that Github Copilot may have copied some of the content from other sources, and I have no intention of plagiarizing anyone's work.

Please let me know if you find any mistakes, have any suggestions, or if you find any content that is plagiarized. I will try my best to address those. I hope this helps you in your learning process as well. :wink:


---

## Table of Contents

- [Probability](#probability)


---


# Probability
## Types of Probability
### Marginal Probability
`Marginal Probability` is defined as the likelyhood of an event happening.
$$P(A) = \frac{N(A)}{N(S)}$$
where $N(A)$ is the number of outcomes in the sample space $S$, that are in the event $A$.

### Joint Probability
`Joint Probability` is defined as the likelyhood of two events happening at the same time. Joint probability is the product of the marginal probabilities of the two events, given that they are independent.
$$P(A,B) = \frac{N(A,B)}{N(S)}$$
where $N(A,B)$ is the number of outcomes in the sample space $S$, that are in the event $A$ and $B$, given that `$A$ and $B$ are independent events`.

### Conditional Probability
`Conditional Probability` is defined as the likelyhood of an event happening, given that another event has already happened. It is often calculated for events that are not independent, and `there is some dependency between them`.
$$P(A|B) = \frac{P(A,B)}{P(B)}$$
$$\implies P(A|B) = \frac{N(A,B)}{N(S)}$$
where $P(A,B)$ is the probabability of the event $A$ and $B$ happening at the same time, and $N(A,B)$ is the number of outcomes in the sample space $S$, that are in the event $A$ and $B$ simultaneously.



## Bayes' Theorem
`Bayes' Theorem` is a way to calculate the conditional probability of an event, given that another event has already happened. It is often calculated for events that are not independent, and `there is some dependency between them`.
$$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$
where $N(A,B)$ is the number of outcomes in the sample space $S$, that are in the event $A$ and $B$.


## Concepts in Probability
### Expected Value
`Expectation` or `Expected Value` is defined as the average value of a random variable. For any random distribution, the expectation is the mean of that distribution.
$$E(X) = \sum_{i=1}^{n} x_i p(x_i)$$
where $x_i$ is the value of the random variable, and $p(x_i)$ is the probability of the random variable taking the value $x_i$. The expectation is also the sum of the product of the value of the random variable and the probability of the random variable taking that value.

### Variability
Variability is measured by the `variance` and `standard deviation` of a distribution.

`Deviation` is the difference between the value of a random variable and the expected value of that variable.
$$\text{Deviation} = x - E(x)$$

`Variance` and `Standard Deviation` are two measures of the spread of a distribution. The variance is the average of the squared deviations from the mean, and the standard deviation is the square root of the variance.
$$\text{Variance} = \sigma^2 = \frac{1}{N} \sum_{i=1}^N (x_i - E(x))^2$$
$$\text{Standard Deviation} = \sigma = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - E(x))^2}$$
where $N$ is the number of samples in the distribution.

### Covariance and Correlation
`Covariance` is a measure of the relationship between two random variables. It is the average of the product of the deviations of the two variables from their respective means.
$$\text{Covariance} = \sigma_{xy} = \frac{1}{N} \sum_{i=1}^N (x_i - E(x))(y_i - E(y))$$
where $N$ is the number of samples in the distribution.

`Correlation` is a normalized measure of the relationship between two random variables. It is the covariance of the two variables divided by the product of their standard deviations.
$$\text{Correlation} = \rho_{xy} = \frac{\sigma_{xy}}{\sigma_x \sigma_y}$$
where $\sigma_x$ and $\sigma_y$ are the standard deviations of the two variables.


---


# Random Variables
`Random Variable` is a variable whose value is determined by chance. It is a function that maps the sample space to the real numbers.
$$X: S \rightarrow \mathbb{R}$$
where $X$ is the random variable, $S$ is the sample space, and $\mathbb{R}$ is the set of real numbers.

Some of the common types of random variables are:
## Bernoulli Random Variable
Bernoulli Random Variable is a random variable that can take on the values 0 or 1, with probability $p$ and $1-p$ respectively.
$$X: S \rightarrow \{0,1\}$$
$$P(X=1) = p$$
$$P(X=0) = 1-p$$
where $p$ is the probability of the event happening.
Example: Tossing a coin, occurence of an event, etc.

- `Discrete Random Variable`: A random variable that can take on a finite or countable number of values.
$$X: S \rightarrow \mathbb{N}$$
$$P(X=x_i) = p_{x_i}$$
$$\sum_{i \in S} P(X=x_i) = 1$$
where $x_i$ is the value of the random variable, and $p_{x_i}$ is the probability of the random variable taking on the value $x_i$.

- `Continuous Random Variable`: A random variable that can take on any value in an interval.
$$X: S \rightarrow \mathbb{R}$$
$$P(a \leq X \leq b) = \int_a^b f(x)dx$$
$$\int_{-\infty}^{\infty} f(x)dx = 1$$
where $f(x)$ is the probability density function of the random variable $X$.

Other variations of `Discrete Random Variable` are:
- `Uniform Discrete Random Variable`: A random variable that can take on the discrete values $a, a+1, a+2, ..., b$, with equal probability.
$$X: S \rightarrow \{a,a+1,a+2,...,b\}$$
$$P(X=x) = \frac{1}{b-a+1}$$
$$\sum_{i=a}^b P(X=x_i) = 1$$
where $a$ and $b$ are the lower and upper bounds of the random variable.

- `Uniform Continuous Random Variable`: A random variable that can take on any value in an interval, with equal probability.
$$X: S \rightarrow \mathbb{R}$$
$$P(a \leq X \leq b) = \frac{1}{b-a}$$
$$\int_{-\infty}^{\infty} f(x)dx = 1$$
where $a$ and $b$ are the lower and upper bounds of the random variable.

- `Binomial Random Variable`: A random variable that can take on the values 0, 1, 2, ..., $n$, with probability $p$ and $1-p$ respectively.
$$X: S \rightarrow \{0,1,2,...,n\}$$
- `Poisson Random Variable`: A random variable that can take on the values 0, 1, 2, ..., $\infty$, with probability $p$ and $1-p$ respectively.
$$X: S \rightarrow \{0,1,2,...,\infty\}$$
- `Normal Random Variable`: A random variable that can take on the values $-\infty, -\infty+1, -\infty+2, ..., \infty$, with probability $p$ and $1-p$ respectively.
$$X: S \rightarrow \{-\infty,-\infty+1,-\infty+2,...,\infty\}$$

## Probability Distribution Functions
`Probability Distribution Functions` are functions that map the probability of a random variable to the real numbers. They are also called `Probability Mass Functions` for discrete random variables, and `Probability Density Functions` for continuous random variables.
$$f(x) = P(X=x)$$
where $f(x)$ is the probability distribution function, $P(X=x)$ is the probability of the random variable $X$ taking on the value $x$.

## Discrete Random Variables
### Expected Value for discrete random variables
For a discrete random variable $X$, the expected value is calculated as:
$$E(X) = \sum_{i=1}^{n} {\big[ x_i \cdot P(X=x_i) \big]}$$

### Variance for discrete random variables
For a discrete random variable $X$, the variance is calculated as:
$$Var(X) = E(X^2) - E(X)^2$$
$$\implies Var(X) = \sum_{i=1}^{n} {\big[ x_i^2 \cdot P(X=x_i) \big]} - \big[ \sum_{i=1}^{n} {\big[ x_i \cdot P(X=x_i) \big]} \big]^2$$
$$\implies Var(X) = \sum_{i=1}^{n}{ (x_i-\mu)^2 \cdot P(X=x_i) }$$
where $\mu$ is the mean of the distribution.

### Standard Deviation for discrete random variables
For a discrete random variable $X$, the standard deviation is calculated as:
$$\sigma = \sqrt{Var(X)}$$
where $\sigma$ is the standard deviation of the distribution.

## Continuous Random Variables
### Expected Value for continuous random variables
For a continuous random variable $X$, the expected value is calculated as:
$$E(X) = \int_{-\infty}^{\infty} {x \cdot f(x) \cdot dx}$$
where $f(x)$ is the probability density function of the distribution.

### Variance for continuous random variables
For a continuous random variable $X$, the variance is calculated as:
$$Var(X) = E(X^2) - E(X)^2$$
$$\implies Var(X) = \int_{-\infty}^{\infty} {x^2 \cdot f(x) \cdot dx} - \Bigg[ \int_{-\infty}^{\infty} {x \cdot f(x) \cdot dx} \Bigg]^2$$
$$\implies Var(X) = \int_{-\infty}^{\infty} {x^2 \cdot f(x) \cdot dx} - \mu^2$$
where $\mu$ is the mean of the distribution.

### Standard Deviation for continuous random variables
For a continuous random variable $X$, the standard deviation is calculated as:
$$\sigma = \sqrt{Var(X)}$$
where $\sigma$ is the standard deviation of the distribution.

# Operations on Expectation and Variance
## Covariance
`Covariance` is a measure of how much two random variables vary together. It is calculated as:
$$Cov(X,Y) = E(X,Y) - E(X)E(Y)$$
$$\implies Cov(X,Y) = \sum_{i=1}^{n} {\big[ x_i \cdot y_i \cdot P(X=x_i,Y=y_i) \big]} - \big[ \sum_{i=1}^{n} {\big[ x_i \cdot P(X=x_i) \big]} \big] \big[ \sum_{i=1}^{n} {\big[ y_i \cdot P(Y=y_i) \big]} \big]$$
$$\implies Cov(X,Y) = \sum_{i=1}^{n} {\big[ x_i \cdot y_i \cdot P(X=x_i,Y=y_i) \big]} - \mu_x \mu_y$$
where $\mu_x$ and $\mu_y$ are the means of the distributions of $X$ and $Y$ respectively.

## Correlation
`Correlation` is a measure of how much two random variables vary together. It is calculated as:
$$Corr(X,Y) = \frac{Cov(X,Y)}{\sigma_x \sigma_y}$$
where $\sigma_x$ and $\sigma_y$ are the standard deviations of the distributions of $X$ and $Y$ respectively.

## Linearity of Expectation
For any two random variables $X$ and $Y$, the expectation of the sum of the two random variables is equal to the sum of the expectation of the two random variables.
$$E(X+Y) = E(X) + E(Y)$$
$$E(aX+bY) = aE(X) + bE(Y)$$
where $a$ and $b$ are any constants.

## Linearity of Variance
For any two random variables $X$ and $Y$, the variance of the sum of the two random variables is equal to the sum of the variance of the two random variables, plus the sum of the covariance of the two random variables.
$$Var(X+Y) = Var(X) + Var(Y) + 2Cov(X,Y)$$
$$Var(aX+bY) = a^2Var(X) + b^2Var(Y) + 2abCov(X,Y)$$
where $a$ and $b$ are any constants.

## Product of Expectation
For any two random variables $X$ and $Y$, the expectation of the product of the two random variables is equal to the product of the expectation of the two random variables.
$$E(X,Y) = E(X)E(Y)$$
<br>

## Power of Expectation
For any random variable $X$, the expectation of the power of the random variable is:

$$E(X^n) = \sum_{k=0}^{n} {\frac{n!}{(n-k)!}E(X)^{n-k}Var(X)^k}$$
$$E(X^2) = E(X)^2 + Var(X)$$
$$E(X^3) = E(X)^3 + 3E(X)Var(X) + 2Var(X)^2$$
$$E(X^4) = E(X)^4 + 4E(X)^2Var(X) + 6E(X)Var(X)^2 + 3Var(X)^3$$
$$\vdots$$
$$E(X^n) = E(X)^n + nE(X)^{n-1}Var(X) + \frac{n(n-1)}{2}E(X)^{n-2}Var(X)^2 + \frac{n(n-1)(n-2)}{6}E(X)^{n-3}Var(X)^3 + \cdots + \frac{n!}{(n-k)!}E(X)^{n-k}Var(X)^k + \cdots$$