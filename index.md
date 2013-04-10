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

## Background
- [D4D competition](http://www.d4d.orange.com/home)  to make the most of mobile phone data from Cote d'Ivoir
- How do human mobility and environmental factors drive cholera transmission
 - Most mobility models parameterized using data from North America or Europe.  What about Africa? 
 - Most models forumlated in terms of person-to-person transmission. What can we learn from an environmentally driven model? 
- Opportunity to combine detailed environmental data with mobility data to understand how disease (in this case cholera) are spread.

---

## Human Mobility Models

* Humans (may) follow simple reproducible patterns in thier movements
* Key features:
 * Population / population density
 * Distance between locations
* Gravity Models $\left(pr( i \rightarrow j) \propto P_i^{\alpha}P_j^{\beta}f(d_{ij})\right)$
* Radiation Models (non-parametric)
* Useful for understanding disease dynamics especially in the context of individual-based models

--- &twocol w1:50% w2:50%

## D4D Data Set

* 484,383 individuals observed over different two week periods
* 55,319,911 calls made from 1194 towers

*** left 

```
##      id      call.date.time call.tower
## 2669 23 2011-12-13 20:55:00        863
## 3900 39 2011-12-11 21:10:00        115
## 1561 20 2011-12-07 16:37:00        898
## 4870 44 2011-12-07 07:48:00        414
## 8829 87 2011-12-07 07:03:00        981
## 5063 44 2011-12-15 06:49:00        414
```


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

---

## Towers

<img class="center" src=figures/towers_tesselation.png height="550" width="550">

---

## Our (simple) Mobility Model

* Person k (given their home location) will be seen in any other location at any point in time ($\nu_{i,j}$)
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

<p align="center"><img src=figures/prob_at_home_simple_model_fit.png height="400" width="400"></p>


---
   
## Extensions of the Mobility Model
* Where do people go?
* How long do people stay?
 * frequency of calls from a single location in a day?
 * time between calls in the same location?

---

## Cholera Transmission Model

* Discrete-time Suscuptible Infectious Recovered (SIR) Model
* Country divided into 5-km grid cells
* All infections mediated through environment
 * Cholera infected individuals shed vibrios into "environment"
 * People drink water with some concentration of vibrios from the environment
 * With some probability (dose-response) people get sick

---

## Environmental Factors

<img class="center" src=figures/four_env_plot.png height="500" width="500">

---

## Cholera Simulations

---

## Future Directions and Questions

---



