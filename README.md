

# Multi-Objective Reinforement Learning

slide: https://hackmd.io/@9KCqffEFR4C4AfiS32x7EQ/r1MKItbCI

<br>

---

<br>

# Introduction

<br>

---

<br>

## RL problem

- The learning agent is not provided explicitly what action to take
- The learning agent determines the best action to maximize long-term rewards and execute it
- The selected action makes the current state of the environment to transit into its successive state
- The agent receives a scalar reward signal that evaluates the effect of this state transition
- The agent learns optimal or near-optimal action policies from such interactions in order to maximize some notion of long-term objectives

![](https://i.imgur.com/fNXVuXZ.png)

<br>

---

<br>


### Challenges of RL

Despite of many advances in RL theory and algorithms, one remained challenge is to scale up to larger and more complex problems. 
The scaling problem for sequential decision-making mainly includes the following aspects:

1. Large or continuous state or action space
1. Hierarchically organized tasks and sub-tasks
1. To solve several tasks with different rewards simultaneously

    **Multi-objective reinforcement learning (MORL) problem**

<br>

---

<br>

### Multi-Objective Reinforcement Learning (MORL)

A combination of multi-objective optimization (MOO) and RL techniques to solve the sequential decision-making problems with multiple conflicting objectives

1. Obtain action policies which optimizes two or more objectives at the same time
1. Each objective has its own associated reward signal
1. The reward is not a scalar value but a vector
1. Combine the objectives if they are related
1. Optimize the objectives separately if they are completely unrelated
1. Make a trade-off among the conflicting objectives

<br>

---

<br>

### Multi-Objective Optimization (MOO) Strategies
> Multi-objective to Single-objective Strategy

1. To optimize a scalar value
    * Weighted sum method
    * Constraint method
    * Sequential method
    * Max-min method

    ![](https://i.imgur.com/ZLL6EDA.png)

<br>

> Pareto Strategy

1. Vector-valued utilities 
1. Non-inferior and alternative solutions
1. Constitute the Pareto front

    ![](https://i.imgur.com/MgEaF3f.png)
    ![](https://i.imgur.com/5SElsBk.png)

<br>

---

<br>

### MORL algorithms

> Single-policy Approaches

Find the best single policy specified by a user or derived from the problem domain

<br>

> Multiple-policy Approaches

Find a set of policies that approximate the Pareto front

<br>

---

<br>

# Backgrounds

<br>

---

<br>

## Markov Decision Process (MDP) Models

> A sequential decision-making problem can be formulated as an MDP

S: The state space of a finite set of states

A: The action space of a finite set of actions

R: The reward function

P: The matrix of state transition probability

<br>

> Objective functions

1. Discounted reward criteria
1. Average reward criteria

![](https://i.imgur.com/b5E0sVi.png)

<br>

---

<br>

## MDP Objective Functions 

> Discounted Reward Criteria
> 
![](https://i.imgur.com/3IUIPZJ.png)

> Average Reward Criteria
> 
![](https://i.imgur.com/OcIPSiN.png)

<br>

---

<br>

## Basic RL Algorithms

1. RL algorithms integrate the techniques of Monte Carlo, stochastic approximation, and function approximation to obtain approximate solutions of MDPs
1. As a central mechanism of RL, temporal-difference (TD) learning can be viewed as a combination of Monte Carlo and DP
1. TD algorithms can learn the value functions using state transition data without model information
    - Similar to Monte Carlo methods
1. TD methods can update the current estimation of value functions partially based on previous learned results
    - Similar to DP

<br>

> Discounted Reward Criteria Q-Learning Algorithm

![](https://i.imgur.com/tlGXEUV.png)

<br>

> Average Reward Criteria R-Learning Algorithm

![](https://i.imgur.com/GqSppMn.png)

<br>

---

<br>

## MOO Problems

Maximize the Pareto optimality or the weighted scalar of all the elements and satisfy the constraint functions

![](https://i.imgur.com/zxDNq3O.png)

<br>

---

<br>

## MOO Optimal Solutions

> Multi-objective to Single-objective Strategy

Solutions can be obtained by solving a SOO problem

> Pareto Dominance and Pareto Front

Find all the dominating solutions instead of the dominated ones
Practically, find a set of solutions that approximates the real Pareto front

![](https://i.imgur.com/SZEybJ8.png)

<br>

---

<br>

# MORL Problem

<br>

---

<br>

## Basic Architecture

Maximize the Pareto optimality or the weighted scalar of all the elements and satisfy the constraint functions

![](https://i.imgur.com/DPj9uOM.png)

Vectored state-action value function

![](https://i.imgur.com/7i0qJRK.png)

<br>

---

<br>

## Major Research Topics

1. MORL is a highly interdisciplinary field and it refers to the integration of MOO methods and RL techniques to solve sequential decision making problems with multiple conflicting objectives
1. The related disciplines of MORL include artificial intelligence, decision and optimization theory, operations research, control theory, and so on
1. MORL suitably represents the designer’s preferences or ensure the optimization priority with some policies in the Pareto front
1. Design efficient MORL algorithms

<br>

---

<br>

# Representative Approaches to MORL

<br>

---

<br>

## MORL Approaches

> Single-policy Approaches

1. Weighted sum approach
1. W-learning
1. Analytic hierarchy process (AHP) approach
1. Ranking approach
1. Geometric approach

<br>

> Multiple-policy Approaches

1. Convex hull approach
1. Varying parameter approach

<br>

---

<br>

## Weighted Sum Approach

> GM-Sarsa(0)

1. Sum up the Q-values for all the objectives to estimate the combined Q-function
1. The updates are based on the actually selected actions rather than the best action determined by the value function
1. Has smaller errors between the estimated Q-values and the true Q-values

![](https://i.imgur.com/Po5vLN4.png)

<br>

> Weighted sum approach

![](https://i.imgur.com/xglNRgY.png)

<br>

---

<br>

## W-Learning Approach

> Top-Q method to compute W values

* Assign the W value as the highest Q-value among all the objectives in the current state

![](https://i.imgur.com/aUZBUbz.png)

* Synthetic objective function for the Top-Q approach

![](https://i.imgur.com/R0RWYQw.png)

* The objective with the highest Q-value may have similar priorities for different actions, while other objectives cannot be satisfied due to their low action values
* A change in reward scaling or the design of reward functions may greatly influence the results of the winner-take-all contest

<br>

> W-Learning

* All the W values, except the highest W value, are updated after the action of each step is selected and executed 

![](https://i.imgur.com/Wxc9UNh.png)

<br>

> Negotiated W-Learning

* Explicitly find that if an objective is not 
* preferred to determine the next action
* Might lose the most long-term reward

![](https://i.imgur.com/0dZKUjT.png)

<br>

---

<br>

## Analytic Hierarchy Process (AHP) Approach

* The designer of MORL algorithms may not have enough prior knowledge about the optimization problem
* The degree of relative importance between two objectives can be quantified by L grades, and a scalar value is defined for each grade
* Requires a lot of prior knowledge of the problem domain

Relative importance matrix

![](https://i.imgur.com/4WoDZU4.png)

Importance factor

![](https://i.imgur.com/17KRCkG.png)

Value of improvement

![](https://i.imgur.com/FWJR3vM.png)

Fuzzy inference system: compute the goodness of 𝑎~𝑝~  relative to 𝑎~𝑞~

<br>

---

<br>

## Ranking Approach

* Also called the sequential approach or the threshold approach
* Ensure the effectiveness of the subordinate objective
* Threshold values were specified for some objectives in order to put the constraints on the objectives

![](https://i.imgur.com/1psjKrM.png)

![](https://i.imgur.com/sX9UgY3.png)

<br>

---

<br>

## Geometric Approach

* Deal with dynamic unknown Markovian environments with long-term average reward vectors
* Assume that actions of other agents may influence the dynamics of the environment and the game is irreducible or ergodic

> Multiple directions RL (MDRL) and single direction RL (SDRL)

Approximate a desired target set in a multidimensional objective space

![](https://i.imgur.com/NXUotPp.png)

<br>

---

<br>

## Convex Hull Approach

* Simultaneously learn optimal policies for all linear preference assignments in the objective space
* Can find the optimal policy for any linear preference function
* Since multiple policies are learned at once, the integrated RL algorithms should be off-policy algorithms

Definition 1: Translation and scaling operations

![](https://i.imgur.com/c9kteMr.png)

Definition 2: Summing two convex hulls

![](https://i.imgur.com/2oZoLCC.png)

<br>

![](https://i.imgur.com/krUuxse.png)

<br>

---

<br>

## Varying Parameter Approach

* A multiple-policy approach can be realized by performing multiple runs with different parameters, objective thresholds, and orderings in any single-policy algorithm

> Policy gradient methods and the idea of varying parameters

* Estimate multiple policy gradients for each objective
* Vary the weights of the objective gradients to find multiple policies

<br>

---

<br>

## Summary

> Multi-objective fitted Q-iteration (FQI)

Find control policies for all the linear combinations of preferences assigned to the objectives in a single training procedure

![](https://i.imgur.com/2qNRsIK.png)

<br>

---

<br>

# Important Directions of Recent Research on MORL

<br>

---

<br>

## Further Development of MORL Approaches

> To obtain suitable representations of the preferences and improve the efficiency of MORL algorithms

* Estimation of distribution algorithms (EDA)
    * Incorporate the notions in evolutionary MOO
    * Acquire various strategies by a single run
* Learning classifier system
    * The choice of action-selection policies can greatly affect the performance of the learning system
* α-domination strategy
    * Use a goal-directed bias based on the achievement level of each evaluation
* Parallel genetic algorithm (PGA)
    * Evolve a neuro-controller
    * Perturbation stochastic approximation (SPSA) was used to improve the convergence
* Adaptive margins

> To obtain Pareto optimal policies in large or continuous spaces

* Multi-agent framework
    * ie. Traffic signal control
* Fitted Q-iteration (FQI)
    * Approximate the Pareto front
* Consistency multi-objective dynamic programming

<br>

The small scale of previous MORL problems may not verify the algorithm’s performance in dealing with a wide range of different problem settings, and the algorithm implementations always require much prior knowledge about the problem domain

