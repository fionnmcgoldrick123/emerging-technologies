# Emerging Technologies Assessment Classical and Quantum Algorithms

## Overview

This repository contains a comprehensive exploration of classical and quantum algorithms, focusing on the [Deutsch-Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa) and its predecessor, [Deutsch's algorithm](https://quantum.cloud.ibm.com/learning/en/courses/fundamentals-of-quantum-algorithms/quantum-query-algorithms/deutsch-algorithm). The [problems.ipynb](problems.ipynb) notebook demonstrates the fundamental differences between classical and quantum approaches to determining whether [Boolean functions](https://en.wikipedia.org/wiki/Boolean_function) are constant or balanced, showcasing one of the earliest proven quantum computational advantages.

The notebook progresses through five interconnected problems that build understanding from classical function generation to full quantum algorithm implementation. Beginning with Python-based classical solutions, it transitions to quantum circuit design using [Qiskit](https://www.ibm.com/quantum/qiskit), ultimately demonstrating how quantum computers can solve certain problems exponentially faster than their classical counterparts. Each problem includes detailed theoretical background, implementation code, comprehensive testing, and analysis of efficiency and limitations.

## Assessment Brief

## Repository Contents

- **[problems.ipynb](problems.ipynb)**: The main Jupyter notebook containing all five problems exploring classical and quantum algorithms, with detailed implementations, explanations, tests, and analysis. This notebook progresses from classical Boolean function generation through the implementation of Deutsch's and Deutsch-Jozsa algorithms.

- **[README.md](README.md)**: This file, provides an overview of the project, setup instructions, solution summaries, and references.

- **[requirements.txt](requirements.txt)**: Lists all Python package dependencies required to run the notebook, including Qiskit, Jupyter, NumPy, and Matplotlib.

- **[.gitignore](.gitignore)**: Specifies which files and directories Git should ignore (e.g., virtual environments, Python cache files).

## Repository Structure 

## Setup

This section explains how to set up your computer to run the notebook.

### Requirements

You need the following installed on your computer:

- **Python 3.8 or newer**: The programming language used in this project
- **pip**: Python's package installer (comes with Python)
- **Git** (optional): To download this repository

### Installation

Follow these steps to get everything working:

1. **Download the repository**: If you have Git, open a terminal and run:
   ```bash
   git clone https://github.com/fionnmcgoldrick123/emerging-technologies.git
   cd emerging-technologies
   ```
   Or download the ZIP file from GitHub and extract it.

2. **Create a virtual environment** (recommended): This keeps the project's packages separate from your other Python projects:
   ```bash
   python -m venv .venv
   ```

3. **Activate the virtual environment**:
   - On Windows:
     ```bash
     .venv\Scripts\activate
     ```
   - On Mac/Linux:
     ```bash
     source .venv/bin/activate
     ```

4. **Install the required packages**: This installs all the libraries needed for the notebook:
   ```bash
   pip install -r requirements.txt
   ```

The main packages you'll be using include:
- **Jupyter**: For running notebook files
- **Qiskit**: IBM's quantum computing framework
- **NumPy**: For working with numbers and arrays
- **Matplotlib**: For creating charts and visualizations

### Running The Notebook

Once everything is installed, you can open and run the notebook:

1. Make sure your virtual environment is activated (see step 3 above)

2. Start Jupyter Lab:
   ```bash
   jupyter lab
   ```
   Or if you prefer Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

3. Your web browser will open automatically. Click on [problems.ipynb](problems.ipynb) to open the notebook.

4. Run the code cells by clicking on them and pressing `Shift + Enter`, or use the "Run" button at the top.

**Note**: The notebook uses Python's built-in libraries like `random`, `itertools`, and `typing` for the classical algorithm problems, then transitions to Qiskit for the quantum computing portions.

## Solution Summary

### Problem 1: Generating Random Boolean Functions

Implements `random_constant_balanced()`, a Python function that generates random constant or balanced Boolean functions with four inputs. Constant functions always return the same value (True or False), while balanced functions return True for exactly half (8 of 16) of the possible input combinations. The implementation uses dictionary-based lookup tables and Python's itertools to efficiently generate all 16 possible input combinations, providing the foundation for testing both classical and quantum algorithms.

### Problem 2: Classical Testing for Function Type

Develops `determine_constant_balanced()`, a classical algorithm that determines whether a given Boolean function is constant or balanced. The analysis proves that classical computers require up to 2^(n-1) + 1 queries in the worst case (9 queries for 4-input functions) to be 100% certain of the function type. This establishes the classical baseline that quantum algorithms aim to improve upon, demonstrating the fundamental limitations of classical query complexity.

### Problem 3: Quantum Oracles

Creates quantum oracles for all four single-input Boolean functions (f₀, f₁, f₂, f₃) using Qiskit. Each oracle implements the reversible transformation |x⟩|y⟩ → |x⟩|y ⊕ f(x)⟩ using quantum gates (X, CNOT). The implementation demonstrates key quantum computing principles including reversibility, the XOR trick for preserving quantum information, and how classical functions are encoded as unitary quantum operations. All oracles are verified through comprehensive testing on quantum simulators.

### Problem 4: Deutsch's Algorithm with Qiskit

Implements Deutsch's algorithm, which solves the constant vs. balanced problem for single-input functions with just one oracle query—a 50% reduction from the classical requirement of two queries. The quantum circuit uses superposition and quantum interference to extract global properties of the function. By preparing the output qubit in the |−⟩ state and the input qubit in the |+⟩ state, the algorithm exploits phase kickback to encode the function's type in the final measurement outcome.

### Problem 5: Scaling to the Deutsch–Jozsa Algorithm

Extends Deutsch's algorithm to handle multi-input functions, specifically the 4-input Boolean functions from Problem 1. The Deutsch-Jozsa algorithm maintains the single-query advantage even as the input size grows, representing an exponential speedup over classical approaches (1 query vs. 9 queries for 4 inputs). The implementation demonstrates how oracles for complex Boolean functions are constructed and how the quantum Fourier transform-like interference pattern enables efficient function classification on quantum hardware.

## Results

## References

## Author
*This notebook was written and designed by Fionn McGoldrick*