# Adiabatic Quantum Computing: Maximum Independent Set (MIS)

This repository contains the code and analysis for Practice 1 of the Quantum Computing course. The project serves as an introduction to the D-Wave Ocean SDK and focuses on solving the Maximum Independent Set (MIS) problem using both classical solvers and hybrid quantum approaches.

## Objective

The main objective of this practice is to understand how to map graph theory problems into a format compatible with quantum annealers. Specifically:

1.  Understand the Maximum Independent Set (MIS) problem.
2.  Model the problem as a QUBO (Quadratic Unconstrained Binary Optimization).
3.  Use the `networkx` library for graph generation and visualization.
4.  Solve the problem using different samplers provided by D-Wave (`ExactSolver`, `SimulatedAnnealing`, and `LeapHybridSampler`).

## Theoretical Background

### The Maximum Independent Set Problem
Given a graph G = (V, E), an independent set is a set of vertices in the graph such that no two vertices in the set are adjacent (connected by an edge). The goal of the Maximum Independent Set problem is to find the independent set with the largest possible number of vertices.

### QUBO Formulation
To solve this using adiabatic quantum computing, the problem is formulated as an energy minimization problem.

The objective is to maximize the number of selected nodes while penalizing the selection of two connected nodes. In QUBO format (minimization), this is expressed as:

H(x) = -A * sum(x_i) + B * sum(x_i * x_j for (i, j) in E)

Where:
* x_i is a binary variable (1 if node i is selected, 0 otherwise).
* The first term (-A) incentivizes including nodes in the set (since we want to maximize size, we minimize the negative sum).
* The second term (+B) applies a large penalty if two connected nodes are selected simultaneously (violating the independence constraint).
* B must be greater than A to ensure valid solutions are preferred over larger but invalid sets.

## Project Structure

The notebook `PR1GustavoGarciaIgnacioLopez.ipynb` covers the following steps:

### 1. Graph Generation
* Creation of random graphs using the `networkx` library (e.g., Erdos-Renyi model).
* Visualization of the graph structure to understand the node connections.

### 2. Classical Exact Solution
* Usage of `dimod.ExactSolver`.
* This solver explores all possible states (brute force) to find the global optimum.
* It is used as a baseline for correctness but is limited to very small graphs due to exponential time complexity.

### 3. Heuristic Solution (Simulated Annealing)
* Usage of `dwave-neal.SimulatedAnnealingSampler`.
* A classical probabilistic technique that mimics the annealing process to find global optima in a large search space.
* Allows solving larger graphs than the exact solver.

### 4. Hybrid Quantum Solution
* Usage of `dwave.system.LeapHybridSampler`.
* Utilizes D-Wave's cloud hybrid solvers, which combine classical computation with quantum annealing to handle larger and more complex problem instances efficiently.

## Requirements and Installation

This project relies on Python and the D-Wave Ocean software stack.

### Prerequisites
* Python 3.8+
* Jupyter Notebook

### Installation
Execute the following command to install the required dependencies:

pip install numpy matplotlib networkx dimod dwave-system dwave-ocean-sdk

## Usage

1.  Clone this repository.
2.  Ensure you have a valid API token configured for the D-Wave Leap cloud service if running the hybrid sampler sections.
3.  Open the notebook:
    jupyter notebook PR1GustavoGarciaIgnacioLopez.ipynb
4.  Execute the cells to generate graphs and run the different optimization algorithms.

## Key Results

* **Formulation:** Successfully mapped the graph problem to a Binary Quadratic Model (BQM).
* **Verification:** The solutions returned by the solvers were verified to ensure that no two nodes in the result set shared an edge.
* **Performance:** Comparison between the execution time and feasibility of exact methods versus heuristic and hybrid methods on different graph sizes.

## Authors

* Gustavo Garcia
* Ignacio Lopez
