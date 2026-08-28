# The Logistic Map as a Markov Chain

Deterministic chaos, coarse-grained into a stochastic approximation, with a check on how good that approximation actually is.

## Overview

This project studies the logistic map as a chaotic dynamical system, then asks how well a finite-state Markov chain (via Ulam's method) can approximate it. It connects two areas that may not usually meet: dynamical systems theory # and numerical linear algebra. The throughline is a deterministic system whose Markov-chain approximation converges to a known closed-form stationary distribution.

## Contents

- `chaos_prob.ipynb`: main notebook, from orbit generation through to convergence analysis
- `logistic_map_writeup.pdf`: derivations backing the numerical results

## What's in the notebook

1. **Logistic map and orbit generation**: the base dynamical system.
2. **Fixed points, linear stability, bifurcation diagram**: tracing the period-doubling route to chaos.
3. **Feigenbaum constant extraction**: estimated from successive bifurcation spacings.
4. **Lyapunov exponent computation**: quantifying sensitivity to initial conditions.
5. **Invariant density**: characterised at the fully chaotic parameter value against its closed form.
6. **Ulam's method, two constructions**:
   - Orbit-based: the transition matrix is built from a long trajectory's visitation statistics.
   - Exact: the transition matrix is built analytically from the map's two inverse branches, using interval arithmetic.
   - Both stationary distributions (via power iteration) are compared against the closed-form invariant density.
7. **Convergence analysis**: how the approximation error behaves as the number of discretisation states grows.

## Headline result

The two constructions behave differently as the state count grows. The orbit-based version gets worse, because a fixed-length sample is being subdivided ever more finely: it's a sampling problem, rather than a discretisation one. The exact construction converges properly, tracking the rate expected from Monte Carlo theory. Reporting both separates sampling error from discretisation error, rather than treating "Ulam's method error" as a single undifferentiated quantity.

## Requirements

- Python: numpy, matplotlib
- LaTeX: `pdflatex`, two-pass compilation

## Running

Restart and Run All in Jupyter reproduces all figures top to bottom.
