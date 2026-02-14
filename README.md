# Emerging Technologies Assessment Classical and Quantum Algorithms

## Overview

This repository contains a comprehensive exploration of classical and quantum algorithms, focusing on the [Deutsch-Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa) and its predecessor, [Deutsch's algorithm](https://quantum.cloud.ibm.com/learning/en/courses/fundamentals-of-quantum-algorithms/quantum-query-algorithms/deutsch-algorithm). The [problems.ipynb](problems.ipynb) notebook demonstrates the fundamental differences between classical and quantum approaches to determining whether [Boolean functions](https://en.wikipedia.org/wiki/Boolean_function) are constant or balanced, showcasing one of the earliest proven quantum computational advantages.

The notebook progresses through five interconnected problems that build understanding from classical function generation to full quantum algorithm implementation. Beginning with Python-based classical solutions, it transitions to quantum circuit design using [Qiskit](https://www.ibm.com/quantum/qiskit), ultimately demonstrating how quantum computers can solve certain problems exponentially faster than their classical counterparts. Each problem includes detailed theoretical background, implementation code, comprehensive testing, and analysis of efficiency and limitations.

## Assessment Brief

## Repository Contents

## Repository Structure 

## Setup
### Requirements
### Instillation
### Running The Notebook

## Solution Summary

### Problem 1: Generating Random Boolean Functions

Implements `random_constant_balanced()`, a Python function that generates random constant or balanced Boolean functions with four inputs. Constant functions always return the same value (True or False), while balanced functions return True for exactly half (8 of 16) of the possible input combinations. The implementation uses dictionary-based lookup tables and Python's itertools to efficiently generate all 16 possible input combinations, providing the foundation for testing both classical and quantum algorithms.

### Problem 2: Classical Testing for Function Type

Develops `determine_constant_balanced()`, a classical algorithm that determines whether a given Boolean function is constant or balanced. The analysis proves that classical computers require up to 2^(n-1) + 1 queries in the worst case (9 queries for 4-input functions) to be 100% certain of the function type. This establishes the classical baseline that quantum algorithms aim to improve upon, demonstrating the fundamental limitations of classical query complexity.

### Problem 3: Quantum Oracles

Creates quantum oracles for all four single-input Boolean functions (f₀, f₁, f₂, f₃) using Qiskit. Each oracle implements the reversible transformation |x⟩|y⟩ → |x⟩|y ⊕ f(x)⟩ using quantum gates (X, CNOT). The implementation demonstrates key quantum computing principles including reversibility, the XOR trick for preserving quantum information, and how classical functions are encoded as unitary quantum operations. All oracles are verified through comprehensive testing on quantum simulators.

### Problem 4: Deutsch's Algorithm with Qiskit


### Problem 5: Scaling to the Deutsch–Jozsa Algorithm


## Results

## References

## Author
*This notebook was written and designed by Fionn McGoldrick*