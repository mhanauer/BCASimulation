---
title: "ECLS-K-2011"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
Simulations in r

Predict the number of girls in 400 births with a 48.8% of being female
```{r}
n.girls = rbinom(1,400,.488)
# Now get a distributions of the number of girls in 400 births over a 1,000 simulations

n.sims = 1000

n.girls.sim = rbinom(n.sims, 400, .488)
hist(n.girls)
mean(n.girls)

data = data.frame(y = rnorm(100), x1 = rnorm(100))
data.lm = lm(y ~ x1, data = data)
data.pred = predict(data.lm)
exp(data.pred)
data.pred

```
Here we have a range of x's draw from a normal random and the same with error term.  Number of x's needs to match number of error's.  For BCA, the x's would be the data we have costs.  Get a random distribution of cost1.  Then replicate these findings 1000 times producing 10,000 possible data point.  We are assuming b1 is 1 meaning that there is a linear relationship between the two.  
```{r}
# Assume that a cost that we have is drawn from a random sample with a mean cost of $5 and an sd of 1
set.seed(20)
cost1 = rnorm(100,5,1)
cost1 = replicate(1000, cost1)
cost1 = sample(cost1, 100)
b1 = 1
b = 0
e = rnorm(length(cost1))
y = b + b1*cost1 + e
mean(y)

```

