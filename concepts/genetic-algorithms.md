---
tags:
  - concept
  - ece459
  - runtime-optimization
lectures:
  - L20
prerequisites:
  - "[[observe-and-change]]"
---

# Genetic Algorithms

A genetic algorithm is an optimization technique inspired by natural selection. A number of candidate solutions are created (usually randomly) and evaluated using a fitness function that measures how well they solve the problem. Solutions with higher fitness have a higher chance of surviving into the next generation. At each generation, good solutions are combined (crossover) and/or randomly mutated. This repeats until a sufficiently good solution is found or a fixed number of generations have been evaluated.

In the context of programming for performance, genetic algorithms are useful for optimizing configuration parameters when the parameter space is large and the interactions between parameters are nonlinear -- meaning you cannot treat each parameter independently. A concrete example is tuning a route-finding system like Google Maps, where parameters might include the number of routes to evaluate, traffic information decay, time-of-day weighting, and search radius. Manually choosing these values is impractical, especially when they should vary by context.

Genetic algorithms require a continuous or discrete fitness function (not binary pass/fail) so that solutions can be ranked. They do not guarantee finding the global optimum -- the fitness landscape may have local maxima. Additionally, if the fitness function is expensive to evaluate or can only be evaluated infrequently, convergence can be slow. Despite these limitations, genetic algorithms are a practical approach to self-optimizing software when brute-force search of the parameter space is infeasible.

## Prerequisites

- [[observe-and-change]] — Genetic algorithms are an advanced form of runtime parameter tuning

## Lectures

- [[L20-Self-Optimizing-Software]]

## Related Concepts

- [[observe-and-change]]
- [[binary-rewriting]]
- [[plan-caching]]
