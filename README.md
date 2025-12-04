# Quantum Computing Practice 1: Modeling and Visualization of Quantum Noise Channels

This repository contains the code and analysis developed for **Practice 1** of the Quantum Computing Laboratory. The project focuses on the simulation and analysis of the impact of different **Quantum Noise Channels** on a single qubit state, utilizing the density matrix representation and visualization on the Bloch Sphere.

## Objective

The main goal of this practice is to understand and simulate the effects of decoherence and noise within a single-qubit quantum system. The key objectives are:

1.  Model the state of a qubit using the **Density Matrix** formalism ($\rho$).
2.  Implement and apply the operators for the principal **Quantum Noise Channels**.
3.  Geometrically visualize the evolution of quantum states under noise using the **Bloch Sphere**.
4.  Analyze the contraction of the Bloch sphere vector as a measure of state purity loss.

## Theoretical Background

Noise is the primary obstacle to large-scale quantum computation (NISQ era). It is modeled by **Quantum Channels**, which describe how interaction with the environment degrades a pure state into a mixed state.

The effect of a quantum channel $\mathcal{E}$ on a density matrix $\rho$ is given by the Kraus operators $K_i$:
$$\mathcal{E}(\rho) = \sum_i K_i \rho K_i^{\dagger}$$

### Simulated Quantum Channels

The notebook analyzes three fundamental channels in detail:

1.  **Bit-Flip Channel (X-error):**
    * Introduces a bit inversion error (Pauli X operation) with probability $p$.
    * Primarily affects coherence along the Y and Z axes, contracting the Bloch vector towards the X-axis.

2.  **Phase-Flip Channel (Z-error):**
    * Introduces a phase error (Pauli Z operation) with probability $p$.
    * Primarily affects coherence along the X and Y axes, contracting the Bloch vector towards the Z-axis.

3.  **Depolarizing Channel:**
    * Mixes the qubit state uniformly with the maximally mixed state ($I/2$).
    * Results in an isotropic (uniform in all directions) contraction of the Bloch vector toward the origin.

### Geometric Interpretation

On the Bloch Sphere, the **amount of noise** is visualized as a contraction of the state vector ($\vec{r}$) toward the center. The length of the vector $|\vec{r}|$ is directly related to the **purity** of the state: the closer the vector endpoint is to the origin, the more mixed and noisy the state.

## Project Structure

The notebook `PR1GustavoGarciaIgnacioLopez.ipynb` is organized into the following logical sections:

1.  **Classical Noise Introduction:** Initial definitions and basic modeling concepts.
2.  **Channel Implementation:** Python code to implement and apply the mathematical operations for the Bit-Flip, Phase-Flip, and Depolarizing channels.
3.  **Bloch Sphere Visualization:** Generation of 3D plots illustrating the trajectory of an initial state (e.g., $|+\rangle$) as the error probability ($p$) increases.
4.  **Analysis and Conclusions:** Discussion on the differing nature and impact of each noise type on the geometry of the quantum state.

## Requirements and Installation

This project relies on Python and standard libraries for numerical analysis and visualization. The use of Qiskit's utilities for quantum states is strongly recommended (or similar libraries like QuTiP).

### Prerequisites
* Python 3.8+
* Jupyter Notebook

### Installation of Dependencies
Execute the following command to install the required libraries (assuming usage of a quantum framework like Qiskit, NumPy, and Matplotlib):

```bash
pip install numpy matplotlib qiskit
