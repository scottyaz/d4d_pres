---
title       : Human Mobility and Cholera Transmission
subtitle    : Insights from Mobile Phone Data from the D4D competition
author      : Andrew Azman (with Justin Lessler)
job         : http://scottyaz.github.io/d4d_pres/
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

<img class="center" src=figures/d4dscreen.png height="600" width="900">


---

## Motivation
- What role do human mobility and local environmental conditions play in cholera transmission?
 - North American/European vs. African mobility patterns
 - Person-to-person vs. environmentally mediated transmission

--- 
## Human Mobility Models

<img class="center" src=figures/zipf_and_newton.jpg height="315" width="500">

--- 

## Human Mobility Models
* Humans (may) follow simple reproducible patterns in their movements
* Key predictors:
 * Population / population density
 * Distance between locations
* Gravity Models $\left(pr( i \rightarrow j) \propto \frac{P_i^{\alpha}P_j^{\beta}}{f(d_{ij})}\right)$
* Radiation Models (non-parametric)
* Useful for understanding disease dynamics especially in the context of individual-based models

--- &twocol w1:50% w2:50%

## D4D Data Set

* 500,000 individuals observed over different two week periods
* 55,319,911 calls made from ~1200 towers

*** left 

```
##      id      call.date.time call.tower
## 8778 86 2011-12-12 22:38:00        299
## 3408 31 2011-12-10 12:25:00        172
## 5036 44 2011-12-13 11:48:00        299
## 8786 86 2011-12-12 22:39:00        299
## 6894 61 2011-12-11 12:29:00        182
## 5277 48 2011-12-08 07:26:00        169
```


---

<img class="center" src=figures/towers_tesselation.png height="550" width="600">

--- &twocol w1:50% w2:50%

*** left
<p></p>
<p></p>
<p></p>
<img class="center" src=figures/calls_per_person.png height="500" width="500">

*** right

<p></p>
<p></p>
<p></p>
<img class="center" src=figures/time_between_calls50.png height="500" width="500">

--- &twocol w1:50% w2:50%

*** left

<p></p>
<p></p>
<p></p>
<img class="center" src=figures/disp_hist_no_zeros_freq.png height="500" width="500">

*** right

<p></p>
<p></p>
<p></p>
<img class="center" src=figures/home_disp_ecdf.png height="500" width="500">

---

## Our (simple) Mobility Model

* Person $k$ (given their home location $i$) will be seen in any other location at any point in time with probability $\nu_{i,j}$
\[ 
\begin{align}
 logit(\nu_{i,j}) = 
    \left\{
 \begin{array}{ll}
		 \alpha_0 + \alpha_1
  log(P_i)  & \mbox{if } i  = j \\
		 \alpha_2 + \alpha_3
  log(P_i) + \alpha_4 log(P_j) + \alpha_5 log(d_{ij}) & \mbox{if } i \neq j
	\end{array}
\right.
\end{align}
\]
* Challenges:
 * Depends on home location
 * Assumes trips always made from home to different locations

---

## Model Fit

 quantile | $\alpha_0$ | $\alpha_1$ | $\alpha_2$ | $\alpha_3$ | $\alpha_4$ | $\alpha_5$ 
  --------|------------|------------|-----------|--------------|-----------|------------
  2.5% | 1.8704 | -0.1603 | -6.9926 | 0.0229 | 0.2897 | -1.1270 
  50% | 1.8791 | -0.1594 | -6.9815 | 0.0239 | 0.2905 | -1.1266  
  97.5% | 1.8876 | -0.1584 | -6.9707 | 0.0249 | 0.2913 | -1.1262  

<img class="center" src=figures/prob_at_home_simple_model_fit.png height="400" width="400">

---

## Cholera Transmission Model

* Discrete-time Susceptible Infectious Recovered (SIR) model
* Country divided into 5-km grid cells
* All infections mediated through environment
 * Cholera infected individuals shed vibrios into "environment"
 * People drink water with some concentration of vibrios from the environment
 * With some probability (dose-response) people get sick

---

## Environmental Mediators of Transmission

<img class="center" src=figures/four_env_plot.png height="500" width="500">

---

## Cholera Simulations

<img class="center" src=figures/run5_3.png height="500" width="600">
<h4><a href="http://andrewazman.com/D4D/movies/run3">example simulation</a></h4>

---

## Cholera Simulations

<img class="center" src=figures/arrival_time_run2.png height="500" width="400">

---

## Future Directions

* Improve movement model
  * How to learn about duration
  * Simulations to understand potential biases
* Refine functional form of environmental modifiers 
* Fit to cholera data 
* Exploration of general epidemiologic connectivity of areas within country

--- 

## Links
* [netmob](http://perso.uclouvain.be/vincent.blondel/netmob/2013/)
* [kaggle](http://www.kaggle.com/)
* [d4d](http://www.d4d.orange.com)
