---
published: false
---
# Bayesian Vs. Frequentist Statistics

Bayesian Vs. Frequentist Statistics

## What’s the difference?

Let’s consider an example situation where a person has misplaced their cellphone. Now, let’s see how this situation plays under frequentist and bayesian considerations:

## Frequentist:
The person assumes that they must have misplaced their cellphone somewhere in their home. Because usually, the person has their cellphone, not in silent mode, it would be easy to find their cellphone by calling from another cellphone. Following the assumptions, they decide to ring their cellphone and figure out where the sound of the ringtone comes from. 

Example: Let’s assume we flipped a coin at random and it ended up heads with probability p (p is unknown). We decided to calculate the value of p by conducting 14 trials (i.e., flipped the coin 14 times). It ended up heads 10 times. We like to challenge ourselves :) and so we question:
What is the probability of getting heads in the next two tosses in a row?

Using frequentist statistics we would say that the best (maximum likelihood) estimate for 

p = 10/14
p ≈ 0.714

In this case, the probability of two heads is (0.714)^2 ≈ 0.51 (because each event is independent we multiply the probabilities). So here we are not updating our knowledge about the probability between the two trials.

## Bayesian:
Instead of assuming that they must have misplaced their cellphone at home, they start thinking about the places where they had misplaced in the past. Using the prior knowledge they decide to narrow down to a place where it is most likely to find their cellphone. So out of three places: their home, car, and workplace, they decide to start looking for their cellphone in their car as that’s where they had forgetfully placed most often.

Time to get a bit geekier here using an example. Let’s consider a coin-tossing problem.
There are two types of coins that have different probabilities of landing heads when tossed.

- Type A coins are fair, with a probability 0.5 of heads
- Type B coins are bent and have a probability 0.6 of heads

We have a drawer that has 5 coins in total comprising 2 coins of Type A and 3 coins of Type B. We pick a coin at random and flip it and it lands on heads. Now the challenge is to find the probability that the coin is Type A or Type B given that we have gotten heads while flipping? I.e., we have to figure out P(A|D) and P(B|D)?

Let A and B be the event that the chosen coin was Type A and Type B. Let D be the event that the toss ended up heads. The problem asks us to find P(A|D), P(B|D).


According to Bayes theorem, we can represent P(A|D) as:

****P(A|D) = (P(D|A) * P(A)) / P(D)


Likewise P(B|D) as: 

****P(B|D) = (P(D|B) * P(B)) / P(D)


Before applying Bayes’ theorem, let’s introduce some terminology:

**D (or data):** the result of our experiment or the data. In this case the resulting event D = ‘heads’. We think of D as data that provides evidence for or against each hypothesis.
Hypotheses: we are testing two hypotheses: the coin is type A or B.

**Prior probability:** the probability of each hypothesis prior to tossing the coin (collecting data). Since the drawer has 2 coins of type A and 3 of type B and 1 or type C we have 
P(A) = 0.4
P(B) = 0.6

**Likelihood:** is the probability of data assuming that the hypothesis is true. And hypothesis in this context is whether the coin is Type A or Type B.

P(D|A) is the probability of heads if the coin is type A
P(D|B) is the probability of heads if the coin is type B

In our case the likelihoods are:
P(D|A)=0.5 (because Type A coins are fair)
P(D|B)=0.6 (because Type B coins are bent)

**Posterior probability:** the probability, posterior to, of each hypothesis given the data from tossing the coin.

P(A|D) and P(B|D) as posterior probabilities. These are what we are going to find using Bayes formula mentioned above.

**Calculation:**

The denominator P(D) is computed using the law of total probability where: 

P(D) = P(D|A) * P(A) + P(D|B) * P(B)
     = (0.5 * 0.4) + (0.6 * 0.6)
     = 0.56

Now each of the two posterior probabilities can be computed:

P(A|D) = (P(D|A) * P(A)) / P(D)
       = (0.5 * 0.4) / 0.56
       = 0.3571

P(B|D) = (P(D|B) * P(B)) / P(D)
       = (0.6 * 0.6) / 0.56
       = 0.6429

Let’s put all the values together in a Bayesian table:
Hypothesis
(H)
Prior
P(H)
Likelihood
P(D|H)
Bayes numerator
P(D|H) * P(H)
Is nothing but 
(prior * likelihood)
Posterior
P(H|D)
A
0.4
0.5
0.2
0.3571
B
0.6
0.6
0.36
0.6429

So from the table, coin B is now the most probable as its probability has increased from a prior probability of 0.6 to a posterior probability of 0.6429. Meanwhile, the probability of type A has decreased from 0.4 to 0.3571.

**How does it work?**
It will make a lot of sense when we do a number of trials, say we repeat tossing a coin, picked at random, 5 times. After every trial, we put the coin back in the drawer.
Assume we get heads in the first two trials and turns out the coin is Type A. So for the first trial, the prior of A will be 0.4, but for the second trial, the prior of A will change to 0.3571. In other words, the posterior of A in trial one will become prior of A in trial two. 

**So what are we doing here**? 
Well, we are updating our knowledge about A after the first trial. The process of going from the prior probability to the posterior is called Bayesian updating. It uses the data to alter our understanding of the probability of each of the possible hypotheses.

**Let’s reframe Bayes**
With the data fixed, the denominator P(D) serves to normalize the total posterior probability to 1. So we can also express Bayes theorem as:

****P(hypothesis|data) ∝ P(data|hypothesis) * P(hypothesis)

This leads to the most elegant form of Bayes theorem in the context of Bayesian updating:

****Posterior ∝ Likelihood * Prior

