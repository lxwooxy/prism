# PRISM Learning Projects

This repository contains small projects created using the **PRISM Model Checker**. I'm using these toy examples to learn and experiment with modeling and verifying probabilistic systems.

## Projects Included

1. **Coin Flip**:
   - A simple DTMC model to calculate the probability of flipping heads and expected steps to achieve specific outcomes.
   - Files: `coin_flip.prism`, `coin_flip.props`

2. **Dice Game**:
   - A probabilistic dice game where the goal is to reach a sum of 15, with losing conditions for consecutive rolls of 1.
   - Files: `dice_game.prism`, `dice_game.props`

3. **Random Walk**:
   - A random walk on a finite line with reflective boundaries.
   - Files: `random_walk.prism`, `random_walk.props`

4. **Traffic Light Controller**:
   - A cyclic traffic light system with Green, Yellow, and Red states modeled as a DTMC.
   - Files: `traffic_light.prism`, `traffic_light.props`

5. **Probabilistic Two-State Machine**:
   - A simple DTMC alternating between two states with probabilistic transitions.
   - Files: `probabilistic_two_state.prism`, `probabilistic_two_state.props`

6. **Two-State Machine**:
   - A basic DTMC that alternates deterministically between two states.
   - Files: `two_state.prism`, `two_state.props`

7. **Epidemic Model**:
   - A WIP, at the moment recovered individuals CAN be reinfected. but its not heterogeneous yet. I'm not even sure if PRISM supports arrays tbh.

## Output Files

Each project has an accompanying output file (`*.txt`) containing the results of property verification using PRISM. These include probabilities, expected steps, and steady-state calculations.

## Usage

1. **Install PRISM**: Download and install PRISM from [prismmodelchecker.org](http://www.prismmodelchecker.org/).
2. **Run a Project**:
   - Example for the `coin_flip` project:
     ```bash
     prism coin_flip.prism coin_flip.props > coin_flip_output.txt
     ```
3. **Analyze the Output**:
   - Open the respective output file (e.g., `coin_flip_output.txt`) to review the results of the model checking.

## Example Output: Coin Flip

Here’s an example output from running the **Coin Flip** project:

```plaintext
PRISM
=====

Version: 4.8.1
Date: Sun Nov 17 20:09:35 EST 2024
Hostname: georgina-beepboop.local
Memory limits: cudd=1g, java(heap)=1g
Command line: prism coin_flip.prism coin_flip.props

Parsing model file "coin_flip.prism"...

Type:        DTMC
Modules:     coin
Variables:   s h

Parsing properties file "coin_flip.props"...

1 property:
(1) P=? [ F "got_heads" ]

---------------------------------------------------------------------

Model checking: P=? [ F "got_heads" ]

Building model...

Computing reachable states...

Reachability (BFS): 4 iterations in 0.00 seconds (average 0.000000, setup 0.00)

Time for model construction: 0.032 seconds.

Type:        DTMC
States:      7 (1 initial)
Transitions: 10

Transition matrix: 18 nodes (3 terminal), 10 minterms, vars: 3r/3c

Prob0: 2 iterations in 0.00 seconds (average 0.000000, setup 0.00)

Prob1: 4 iterations in 0.00 seconds (average 0.000000, setup 0.00)

yes = 3, no = 1, maybe = 3

Computing remaining probabilities...
Engine: Hybrid

Building hybrid MTBDD matrix... [levels=3, nodes=14] [0.7 KB]
Adding explicit sparse matrices... [levels=3, num=1, compact] [0.0 KB]
Creating vector for diagonals... [dist=1, compact] [0.0 KB]
Creating vector for RHS... [dist=2, compact] [0.0 KB]
Allocating iteration vectors... [2 x 0.1 KB]
TOTAL: [0.9 KB]

Starting iterations...

Jacobi: 4 iterations in 0.00 seconds (average 0.000000, setup 0.00)

Value in the initial state: 0.875

Time for model checking: 0.009 seconds.

Result: 0.875 (exact floating point)
```
### Explanation:
Property Checked: ```P=? [ F "got_heads" ]```
This computes the probability of eventually flipping a heads starting from the initial state.
### Key Metrics:
```States```: The model has 7 states, with 1 initial state.

```Transitions```: There are 10 possible transitions between states.

```Result```: 0.875 (87.5% probability).
This means there is an 87.5% chance of flipping heads eventually.

## Learning Goals

- Understand the structure of PRISM models.
- Learn to write properties using PCTL.
- Analyze probabilities, rewards, and steady-state behavior.
- Experiment with small, modular projects to build intuition for probabilistic model checking.
