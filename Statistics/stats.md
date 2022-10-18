# :chart_with_upwards_trend: Statistics: Fundamentals

Study Notes on `Fundamental Statistics`, `Probability`, `Distributions`, and `Regression`.

[Sagar Goswami: Github](https://github.com/GoswamiSagarD)



## ToDos
- [ ] Add notes
    - [ ] Sampling Distributions
    - [ ] Hypothesis Testing
    - [ ] ANOVA
    - [ ] Regression
    - [ ] Logistic Regression
- [ ] Add links to resources
- [ ] Add images/diagrams/figures
- [ ] Replace Textbook Definitions with something more intuitive
- [ ] Add some background and context to the notes
- [ ] Add more examples



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
    - [Types of Probability](#types-of-probability)
        - [Marginal Probability](#marginal-probability)
        - [Joint Probability](#joint-probability)
        - [Conditional Probability](#conditional-probability)
    - [Bayes' Theorem](#bayes-theorem)
    - [Concepts in Probability](#concepts-in-probability)
        - [Expected Value](#expected-value)
        - [Variability](#variability)
        - [Covariance and Correlation](#covariance-and-correlation)
        - [Independence](#independence)
- [Random Variables and Distributions](#random-variables-and-distributions)
    - [Discrete Random Variables](#discrete-random-variables)
        - [Expected Value of a Discrete Random Variable](#expected-value-of-a-discrete-random-variable)
        - [Variability of a Discrete Random Variable](#variability-of-a-discrete-random-variable)
        - [Covariance and Correlation of Discrete Random Variables](#covariance-and-correlation-of-discrete-random-variables)
        - [Linear Combination of Discrete Random Variables](#linear-combination-of-discrete-random-variables)
    - [Continuous Random Variables](#continuous-random-variables)
        - [Expected Value of a Continuous Random Variable](#expected-value-of-a-continuous-random-variable)
        - [Variability of a Continuous Random Variable](#variability-of-a-continuous-random-variable)
        - [Covariance and Correlation of Continuous Random Variables](#covariance-and-correlation-of-continuous-random-variables)
        - [Linear Combination of Continuous Random Variables](#linear-combination-of-continuous-random-variables)
- [Distributions](#distributions)
    - [Normal Distribution](#normal-distribution)
        - [Standard Normal Distribution](#standard-normal-distribution)
        - [Z-Score](#z-score)
        - [Probability of a Normal Distribution](#probability-of-a-normal-distribution)
        - [69-95-99.7 Rule](#69-95-997-rule)
    - [Binomial Distribution](#binomial-distribution)
        - [Probability of a Binomial Distribution](#probability-of-a-binomial-distribution)
        - [Normal Approximation of a Binomial Distribution](#normal-approximation-of-a-binomial-distribution)
    - [Poisson Distribution](#poisson-distribution)
        - [Probability of a Poisson Distribution](#probability-of-a-poisson-distribution)




---


# Combinatorics
## Permutation
The number of ways to arrange $k$ objects from a set of $n$ objects is given by the formula:
$$ ^nP_k = \frac{n!}{(n-k)!} $$
## Combination
The number of ways to choose $k$ objects from a set of $n$ objects is given by the formula:
$$ ^nC_k = \frac{n!}{k!(n-k)!} $$




# Probability
Probability is the measure of the likelihood that an event will occur. It is a number between $0$ and $1$, where $0$ represents the impossibility of an event and $1$ represents abosolute certainty of occurence for the event. The probability of an event is denoted by:
$$P(E)$$
where $E$ is the event.

Probability is generally calculated to measure and quantify the uncertainty in the occurence of an event.



## Types of Probability
There are various ways to quantify the probability of an event. The most common ones are:

### Marginal Probability
`Marginal Probability` is defined as the likelyhood of an event happening.
$$P(A) = \frac{N(A)}{N(S)}$$
where $N(A)$ is the number of outcomes in the sample space $S$, that are in the event $A$.


### Joint Probability
`Joint Probability` is defined as the likelyhood of two events happening at the same time. Joint probability is the product of the marginal probabilities of the two events, given that they are independent.
$$P(A,B) = \frac{N(A,B)}{N(S)}$$
where $N(A,B)$ is the number of outcomes in the sample space $S$, that are in the event $A$ and $B$, given that `$A$ and $B$ are independent events`.

#### Independent Events
Two events $A$ and $B$ are said to be independent if the occurence of one event does not affect the occurence of the other event. In other words, the occurence of one event does not change the probability of the other event occuring. For example, if we flip a coin twice, the occurence of getting a head on the first flip does not affect the probability of getting a head on the second flip. In this case, the two events are independent.
To check if two events are independent, we can use the following test:
$$P(A,B) = P(A)P(B)$$
If the above equation holds true, then the two events are independent. Otherwise, they are dependent.

### Conditional Probability
`Conditional Probability` is defined as the likelyhood of an event happening, given that another event has already happened. It is often calculated for events that are not independent, and `there is some dependency between them`.
$$P(A|B) = \frac{P(A,B)}{P(B)}$$
$$\implies P(A|B) = \frac{N(A,B)}{N(B)}$$
where $P(A,B)$ is the probabability of the event $A$ and $B$ happening at the same time, $N(A,B)$ is the number of outcomes in the sample space $S$, that are in the event $A$ and $B$ simultaneously, and $N(B)$ is the number of outcomes in the sample space $S$, that are in the event $B$.



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


### Independence
Two random variables are independent if the probability of one variable does not change when the other variable changes. This means that the covariance of the two variables is zero.
$$\sigma_{xy} = 0$$
$$\text{where, } \sigma_{xy} = \frac{1}{N} \sum_{i=1}^N (x_i - E(x))(y_i - E(y)) = 0$$
where $N$ is the number of samples in the distribution.


---


# Random Variables
`Random Variable` is a variable whose value is determined by chance. It is a function that maps the sample space for values/events/occurences. It can be either discrete or continuous.
$$X: S $$
where $X$ is the random variable, and $S$ is the sample space.

Sample space is the set of all possible outcomes of an experiment. The random variable defined on a sample space, may correspond to various types of `distributions` that defines the sample space.



There are two main types of random variables:
## Discrete Random Variables
`Discrete Random Variable` is a random variable that can take on a finite or countable number of values. `Discrete Distribution` is the distribution of a discrete random variable. The probability of a discrete random variable taking a particular value is defined as the `probability mass function` of the distribution.
$$X: \{x_1, x_2, x_3, \dots, x_n\}$$
$$P(X = x_i) = p_i$$
where $x_i$ is the value of the random variable, and $p_i$ is the probability of the random variable taking the value $x_i$. The sum of the probabilities of all the values of the random variable must be $1$.
$$\sum_{i=1}^n p_i = 1$$


### Expected Value of a Discrete Random Variable
The expected value of a discrete random variable $E(X)$ is the sum of the product of the value of the random variable and the probability of the random variable taking that value.
$$E(X) = \sum_{i=1}^{n} x_i p(x_i)$$
where $x_i$ is the value of the random variable, and $p(x_i)$ is the probability of the random variable taking the value $x_i$. The expectation is also the sum of the product of the value of the random variable and the probability of the random variable taking that value.


### Variability in a Discrete Random Variable
The variance of a discrete random variable $\text{Var}(X)$ or $\sigma_X^2$, is the average of the squared deviations from the mean, and the standard deviation is the square root of the variance.
$$\text{Var}(X) = \sigma_X^2 = \frac{1}{N} \sum_{i=1}^N (x_i - E(x))^2$$
$$\text{Standard Deviation} = \sigma_X = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - E(x))^2}$$
where $N$ is the number of samples in the distribution.


### Covariance and Correlation for Discrete Random Variables
The covariance of a discrete random variable $\sigma_{xy}$ is the average of the product of the deviations of the two variables from their respective means.
$$\text{Covariance} = \sigma_{xy} = \frac{1}{N} \sum_{i=1}^N (x_i - E(x))(y_i - E(y))$$
where $N$ is the number of samples in the distribution.

The correlation of a discrete random variable $\rho_{xy}$ is the covariance of the two variables divided by the product of their standard deviations.
$$\text{Correlation} = \rho_{xy} = \frac{\sigma_{xy}}{\sigma_x \sigma_y}$$


### Linear Combination of Discrete Random Variables
The expected value of a linear combination of two discrete random variables $E(aX + bY)$ is the sum of the product of the value of the random variable and the probability of the random variable taking that value.
$$E(aX + bY) = aE(X) + bE(Y)$$
$$E(aX + bY) = \sum_{i=1}^{n} (ax_i + by_i) p(x_i, y_i)$$
where $a$ and $b$ are constants.

The resulting variance of a linear combination of two discrete random variables $\text{Var}(aX + bY)$ or $\sigma_{aX + bY}^2$ is the sum of the product of the value of the random variable and the probability of the random variable taking that value.
$$\text{Var}(aX + bY) = \sigma_{aX + bY}^2 = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\text{Cov}(X, Y)$$
$$\text{Var}(aX + bY) = \sigma_{aX + bY}^2 = a^2\frac{1}{N} \sum_{i=1}^N (x_i - E(x))^2 + b^2\frac{1}{N} \sum_{i=1}^N (y_i - E(y))^2 + 2ab\frac{1}{N} \sum_{i=1}^N (x_i - E(x))(y_i - E(y))$$



## Continuous Random Variables
`Continuous Random Variable` is a random variable that can take on an infinite number of values. `Continuous Distribution` is the distribution of a continuous random variable. The probability of a continuous random variable taking a particular value is defined as the `probability density function` of the distribution.
$$X: \mathbb{R}$$
$$P(X = x) = f(x)$$
where $x$ is the value of the random variable, and $f(x)$ is the probability density function of the distribution. The sum of the probabilities of all the values of the random variable must be $1$.
$$\int_{-\infty}^{\infty} f(x) dx = 1$$


### Expected Value of a Continuous Random Variable
The expected value of a continuous random variable $E(X)$ is the integral of the product of the value of the random variable and the probability density function of the distribution.
$$E(X) = \int_{-\infty}^{\infty} x f(x) dx$$

To calculate the expected value for a specific range of values, we can use the following formula:
$$E(X) = \int_{a}^{b} x f(x) dx$$
where $a$ and $b$ are the lower and upper bounds of the range.


### Variability in a Continuous Random Variable
The variance of a continuous random variable $\text{Var}(X)$ or $\sigma_X^2$, is the integral of the squared deviations from the mean, and the standard deviation is the square root of the variance.
$$\text{Var}(X) = \sigma_X^2 = \int_{-\infty}^{\infty} (x - E(x))^2 f(x) dx$$
$$\text{Standard Deviation} = \sigma_X = \sqrt{\int_{-\infty}^{\infty} (x - E(x))^2 f(x) dx}$$


### Covariance and Correlation for Continuous Random Variables
The covariance of a continuous random variable $\sigma_{xy}$ is the integral of the product of the deviations of the two variables from their respective means.
$$\text{Covariance} = \sigma_{xy} = \int_{-\infty}^{\infty} (x - E(x))(y - E(y)) f(x, y) dxdy$$

The correlation of a continuous random variable $\rho_{xy}$ is the covariance of the two variables divided by the product of their standard deviations.
$$\text{Correlation} = \rho_{xy} = \frac{\sigma_{xy}}{\sigma_x \sigma_y}$$


### Linear Combination of Continuous Random Variables
The expected value of a linear combination of two continuous random variables $E(aX + bY)$ is the integral of the product of the value of the random variable and the probability density function of the distribution.
$$E(aX + bY) = aE(X) + bE(Y)$$
$$E(aX + bY) = \int_{-\infty}^{\infty} (ax + by) f(x, y) dxdy$$

The resulting variance of a linear combination of two continuous random variables $\text{Var}(aX + bY)$ or $\sigma_{aX + bY}^2$ is the integral of the product of the value of the random variable and the probability density function of the distribution.
$$\text{Var}(aX + bY) = \sigma_{aX + bY}^2 = a^2\text{Var}(X) + b^2\text{Var}(Y) + 2ab\text{Cov}(X, Y)$$
$$\text{Var}(aX + bY) = \sigma_{aX + bY}^2 = \int_{-\infty}^{\infty} (ax + by)^2 f(x, y) dxdy$$




# Distributions
The most common types of distributions observed for random variables are as follows:
## Normal Distribution
The `Normal Distribution` is the most commonly observe distribution for random variables. It is a continuous distribution that is unimodal and symmetric about the mean. It is defined by two parameters, the mean $\mu$ and the standard deviation $\sigma$.
$$X \sim \mathcal{N}(\mu, \sigma)$$

![Normal Distribution](https://upload.wikimedia.org/wikipedia/commons/7/74/Normal_Distribution_PDF.svg)


### Standard Normal Distribution
`Standard Normal Distribution` is a normal distribution with a mean of 0 and a standard deviation of 1.
$$X \sim \mathcal{N}(0, 1)$$


### Z-Score
The `Z-Score` is the number of standard deviations a value is from the mean. It is calculated by subtracting the mean from the value and dividing by the standard deviation.
$$Z = \frac{X - \mu}{\sigma}$$


### Probability of a Normal Distribution
The probability of a normal distribution is the integral of the probability density function from the lower bound to the upper bound.
$$P(a \leq X \leq b) = \int_{a}^{b} f(x) dx$$


### 68-95-99.7 Rule
The `68-95-99.7 Rule` is a rule of thumb that states that:
- 68% of the values of a normal distribution lie within one standard deviation of the mean
- 95% lie within two standard deviations of the mean
- 99.7% lie within three standard deviations of the mean.

In R, to calculate the probability of seeing a value less than or equal to a specific value, we can use the following function:
```r
pnorm(0, mean = 0, sd = 1)
```



## Binomial Distribution
The `Binomial Distribution` is a discrete distribution that is used to model the number of successes $k$ in a sequence of independent trials $n$. It is defined by two parameters, the number of trials $n$ and the probability of success $p$.
$$X \sim \text{Bin}(n, p)$$


### Probability of a Binomial Distribution
The probability of $k$ successes in $n$ trials is given by the following formula:
$$P(X = k) = {^nC}_k \cdot p^k (1 - p)^{n - k}$$
where ${^nC}_k$ is the binomial coefficient, which is the number of ways to choose $k$ items from $n$ items, calculated as:
$${^nC}_k = \frac{n!}{k!(n - k)!}$$


### Normal Approximation of a Binomial Distribution
The `Normal Approximation of a Binomial Distribution` is a normal distribution that approximates the number of successes out of total n traials, where probability of success for indicidual trial is $p$. The expected value or mean, and the variance are given by:
$$ \mu = np \qquad \sigma^2 = np(1 - p) \quad \implies \sigma = \sqrt{np(1 - p)}$$
where $\mu$ is the mean, $\sigma$ is the standard deviation, and $\sigma^2$ is the variance.

It is only used to approximate the binomial distribution when the number of trials $n$ is large enough so that the values of $np$ and $n(1-p)$ are both more than $10$.



## Poisson Distribution
The `Poisson Distribution` is a discrete distribution that is used to model the number of events that occur in a fixed interval of time or space. It is defined by one parameter, the rate $\lambda$ or $\mu$ at which the events occur.
$$X \sim \text{Poisson}(\lambda)$$


### Probability of a Poisson Distribution
The probability of $k$ events occurring in a fixed interval of time or space is given by the following formula:
$$P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$$
where $e$ is the base of the natural logarithms, and $k!$ is the factorial of $k$.


