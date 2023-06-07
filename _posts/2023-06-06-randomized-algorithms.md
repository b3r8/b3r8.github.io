---
title: "Some brief notes about randomized algorithms"
date: 2023-06-06
layout: post
---

In this post, we share some notes about randomized algorithms and related ideas.

<script type="text/javascript" charset="utf-8" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

## Some random stuff

I spent some time the last few months looking for a Randomized Algorithms class to follow online. Luckily, I found the Randomized Algorithms class from UCSC, [CSE290A Spring 2020](https://www.youtube.com/watch?v=sXHr3CDAeWE&list=PLOQjlWvnI0faRpH2oJcyW4CuM5Clt8a2n), by Prof. Sesh Comandur. I’d the pleasure to meet him in person while I was studying at UCSC. I attended and enjoyed his Analysis of Boolean Functions class when I was in SC, so I decided to watch the lectures from his class. 

This post will be an attempt to share a summary of what I consider the most important and interesting ideas from the lectures.

![Randomized algorithm image](/assets/imgs/2023-06-06-post/figure_1_blog_2_craiyon_randomized_algorithm.png){:style="display:block; margin-left:auto; margin-right:auto"}
<h5 align="center"> Figure 1. 'Randomized algorithm', image generated with DALL-E mini model</h5>

## Some important concentration inequalities

- **Markov's inequality**: given a non-negative random variable \\( X \\) and \\( a > 0 \\), then:

\\[ P[X \geq a] \leq \frac{E[X]}{a} \\]

- **Chebyshev's inequality**: given a random variable \\( X \\) with finite non-zero variance \\( \sigma^2 \\) and \\( a > 0 \\), then:

\\[ P[\lvert X - \mu \rvert \geq a\sigma] \leq \frac{1}{a^2} \\]

- **Hoeffding's inequality**: let \\( X_1, ..., X_n \\) be independent random variables such that \\( a_i \leq X_i \leq b_i \\), and \\( S = X_1+...+X_n \\), then for all \\( t > 0 \\):

\\[ P[S - E[S] \geq t] \leq \exp \left(-\frac{2t^2}{\sum (b_i-a_i)^2} \right) \\]
\\[ P[\lvert S - E[S] \rvert \geq t] \leq 2\exp \left(-\frac{2t^2}{\sum (b_i-a_i)^2} \right) \\]

- **Hoeffding's inequality**: let \\( X_1, ..., X_n \\) be independent random variables such that \\( a_i \leq X_i \leq b_i \\), and \\( S = X_1+...+X_n \\), then for all \\( t > 0 \\):

\\[ P[S - E[S] \geq t] \leq \exp \left(-\frac{2t^2}{\sum (b_i-a_i)^2} \right) \\]
\\[ P[\lvert S - E[S] \rvert \geq t] \leq 2\exp \left(-\frac{2t^2}{\sum (b_i-a_i)^2} \right) \\]

- **Generic Chernoff bounds**: given a random variable \\( X \\) and \\( t > 0 \\), we can apply *Markov's inequality* to the random variable \\( e^{tX} \\):

\\[ P[X \geq a] = P[e^{tX} \geq e^{ta}] \leq E[ e^{tX} ]e^{-ta} \\]

Since this bound holds for every positive \\( t \\), we may take the minimum:

\\[ P[X \geq a] \leq \min_{t > 0} E[ e^{tX} ]e^{-ta} \\]

Similarly, for the other tail:

\\[ P[X \leq a] \leq \min_{t < 0} E[ e^{tX} ]e^{-ta} \\]

The quantity \\( E[ e^{tX} ] \\) it's called the **moment-generating function**, and it have some important properties, the most relevant being that it uniquely determines the distribution of \\( X \\).

- **Multiplicative Chernoff bounds**: let \\( X_1, ..., X_n \\) be independent random variables such that \\( X_i \in \{0,1\} \\), let \\( S = X_1+...+X_n \\), and let \\( \mu = E[S] \\). Then for any \\( \delta > 0 \\):

\\[ P[S \geq (1+\delta)\mu] < \left(\frac{e^{\delta}}{(1+\delta)^{1+\delta}} \right)^{\mu} \leq \exp \left(-\frac{\mu\delta^2}{3} \right) \\]

Similarly, for the other tail (for any \\( 1 > \delta > 0 \\)):

\\[ P[S \leq (1-\delta)\mu] < \left(\frac{e^{-\delta}}{(1-\delta)^{1-\delta}} \right)^{\mu} \leq \exp \left(-\frac{\mu\delta^2}{2} \right) \\]

- **Union bound**: let \\( E_1, ..., E_n \\) be a set of events with probabilities \\( P[ E_1 ], ..., P[ E_n ] \\), respectively. Then:

\\[ P left[ \cupE_i \right] \leq \sum P[ E_i ] \\]

Proofs for the majority of the inequalities mentioned can be found in wikipedia.

![Union bound](/assets/imgs/2023-06-06-post/figure_2_blog_2_union_bound.png){:style="display:block; margin-left:auto; margin-right:auto"}
<h5 align="center"> Figure 2. Union bound</h5>

## Approximations to binomial \\( B(n,p) \\) distribution

- **Poisson limit theorem**: if \\( np \\) converges to a finit limit \\( \lambda \\), then Poisson distribution \\( Pois(\lambda) \\) may be used as an approximation to the binomial distribution when \\( n \to \inf \\)

- **de Moivre–Laplace theorem**: Normal distribution \\( \mathcal{N}(np,\,np(1-p)) \\) may be used as an approximation to the binomial distribution when \\( n \to \inf \\) (this is a special case of the [CLT](https://en.wikipedia.org/wiki/Central_limit_theorem))


Until our next post colegas,  
B

## References

- [1] [Lectures playlist](https://www.youtube.com/watch?v=sXHr3CDAeWE&list=PLOQjlWvnI0faRpH2oJcyW4CuM5Clt8a2n)
- [2] [DALL-E mini model](https://www.craiyon.com)
- [3] [Useful Inequalities cheatsheet](https://sites.math.washington.edu/~morrow/335_17/ineq.pdf)
