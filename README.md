# Emerging Technologies: Classical and Quantum Algorithms

## Overview

This repository contains the assessment submission for the Emerging Technologies module (Summer 2025/26) at ATU. The work explores the distinction between classical and quantum approaches to a well-defined computational problem: determining whether a Boolean function is constant or balanced.

The [problems.ipynb](problems.ipynb) notebook works through five interconnected problems, progressing from classical Python implementations to full quantum circuit design using [Qiskit](https://www.ibm.com/quantum/qiskit). The central focus is the [Deutsch-Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa), one of the earliest demonstrations of a provable quantum computational advantage over classical methods.

## Repository Structure

```
emerging-technologies/
├── problems.ipynb      # Main notebook containing all five problems
├── README.md           # This file
├── requirements.txt    # Python package dependencies
└── .gitignore          # Git ignore rules
```

## Problems

The notebook addresses the following five problems in sequence:

**Problem 1: Generating Random Boolean Functions**
Implements `random_constant_balanced()`, a function that randomly generates either a constant or balanced Boolean function over four inputs. Constant functions return the same value for all 16 input combinations; balanced functions return `True` for exactly 8 of them.

**Problem 2: Classical Testing for Function Type**
Implements `determine_constant_balanced()`, a classical algorithm that classifies a given function as constant or balanced. The analysis establishes the worst-case query complexity of 2^(n-1) + 1 calls (9 for four-input functions), forming the classical baseline against which the quantum algorithms are compared.

**Problem 3: Quantum Oracles**
Constructs quantum oracles for all four single-input Boolean functions using Qiskit. Each oracle encodes the function as a reversible unitary transformation of the form |x⟩|y⟩ → |x⟩|y ⊕ f(x)⟩, and is verified on Qiskit's AerSimulator.

**Problem 4: Deutsch's Algorithm**
Implements Deutsch's algorithm for single-input functions. The circuit uses superposition and phase kickback to classify the function as constant or balanced using a single oracle query, compared to the two queries required classically.

**Problem 5: Deutsch-Jozsa Algorithm**
Extends the approach to four-input functions from Problem 1. The Deutsch-Jozsa algorithm classifies any such function using a single oracle query, regardless of input size, demonstrating an exponential improvement over the classical worst case.

## Setup

### Prerequisites

- Python 3.8 or newer
- pip

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/fionnmcgoldrick123/emerging-technologies.git
cd emerging-technologies
python -m venv .venv
```

Activate the virtual environment:

```bash
# Windows
.venv\Scripts\activate

# macOS / Linux
source .venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

### Running the Notebook

```bash
jupyter lab
```

Open [problems.ipynb](problems.ipynb) in the browser and run all cells in order using `Shift + Enter` or the Run All option. The notebook should execute from top to bottom without errors.

Key dependencies include [Qiskit](https://www.ibm.com/quantum/qiskit) and [qiskit-aer](https://github.com/Qiskit/qiskit-aer) for quantum simulation, [NumPy](https://numpy.org/) for numerical operations, and [Matplotlib](https://matplotlib.org/) for circuit and histogram visualisations.

## References

- [Deutsch & Jozsa (1992) - Rapid Solution of Problems by Quantum Computation](https://doi.org/10.1098/rspa.1992.0167)
- [Deutsch (1985) - Quantum Theory, the Church-Turing Principle and the Universal Quantum Computer](https://doi.org/10.1098/rspa.1985.0070)
- [Bernstein & Vazirani (1997) - Quantum Complexity Theory](https://doi.org/10.1137/S0097539796300921)
- [Preskill (2018) - Quantum Computing in the NISQ Era and Beyond](https://doi.org/10.22331/q-2018-08-06-79)
- [Coles et al. (2022) - Quantum Algorithm Implementations for Beginners](https://doi.org/10.1145/3517340)
- [Matuschak & Nielsen (2019) - Quantum Computing for the Very Curious](https://quantum.country/qcvc)
- [Aaronson (2013) - Quantum Computing Since Democritus](https://www.cambridge.org/core/books/quantum-computing-since-democritus/F77C0E5B2E37A0B05BDE0835E582E41E)

- [Python random Module Documentation](https://docs.python.org/3/library/random.html) - *Reference for `random.sample()` used in balanced function generation.*

- [Python itertools.product() Documentation](https://docs.python.org/3/library/itertools.html#itertools.product) - *Reference for generating Cartesian products of input iterables.*

- [Python secrets Module Documentation](https://docs.python.org/3/library/secrets.html) - *Cryptographically secure alternative to `random` for formal analysis.*

- [Quantum Algorithms Revisited - Cleve, Ekert, Macchiavello & Mosca (1998)](https://doi.org/10.1098/rspa.1998.0164) - *Clearest explanation of why classical computation requires exponentially many queries. [arXiv:quant-ph/9708016](https://arxiv.org/abs/quant-ph/9708016).*

- [Quantum Computation and Quantum Information - Nielsen & Chuang (2010)](https://www.cambridge.org/highereducation/books/quantum-computation-and-quantum-information/01E10196D0A682A6802309D06B22D27D) - *Complete proof of the 2^(n-1) + 1 classical query requirement.*

- [Quantum Lower Bounds by Polynomials - Beals, Buhrman, Cleve, Mosca & de Wolf (2001)](https://doi.org/10.1145/502090.502097) - *Formal framework establishing tight query bounds for Deutsch-Jozsa.*

- [Quantum Algorithms: An Overview - Montanaro (2016)](https://doi.org/10.1038/npjqi.2015.23) - *Survey categorizing quantum algorithms by speedup type.*

- [Quantum Computing Lecture Notes - de Wolf (2019)](https://homepages.cwi.nl/~rdewolf/qcnotes.pdf) - *Proves the classical query complexity lower bound from information theory.*

- [Computational Complexity: A Modern Approach - Arora & Barak (2009)](https://theory.cs.princeton.edu/complexity/) - *Covers query complexity and oracle models formally.*

- [Introduction to the Theory of Computation - Sipser (2012)](https://mitpress.mit.edu/9780262018302/) - *Oracle Turing machines and relativized computation foundations.*

- [Introduction to Algorithms - Cormen, Leiserson, Rivest & Stein (2022)](https://mitpress.mit.edu/9780262046305/introduction-to-algorithms/) - *Early termination optimization and computational complexity.*

- [Quantum Supremacy Using a Programmable Superconducting Processor - Arute et al. (2019)](https://doi.org/10.1038/s41586-019-1666-5) - *Practical demonstration of the classical-quantum gap.*

- [Polynomial-Time Algorithms for Prime Factorization and Discrete Logarithms on a Quantum Computer - Shor (1997)](https://doi.org/10.1137/S0097539795293172) - *Builds on the oracle template established by Deutsch-Jozsa.*

- [A Fast Quantum Mechanical Algorithm for Database Search - Grover (1996)](https://doi.org/10.1145/237814.237866) - *Oracle-based quantum speedup achieving quadratic advantage for search.*

- [Python Sets - Real Python](https://realpython.com/python-sets/) - *Reference for tracking distinct output values during classification.*

- [Elementary Gates for Quantum Computation - Barenco et al. (1995)](https://doi.org/10.1103/PhysRevA.52.3457) - *Proves any quantum computation decomposes into single-qubit and CNOT gates.*

- [Logical Reversibility of Computation - Bennett (1973)](https://doi.org/10.1147/rd.176.0525) - *Proves irreversible computation can be embedded in reversible computation, foundational for oracle design.*

- [Reversible Computing - Toffoli (1980)](https://doi.org/10.1007/3-540-10003-2_104) - *Introduces the Toffoli gate and formalizes reversible computation underpinning quantum oracles.*

- [An Introduction to Quantum Error Correction and Fault-Tolerant Quantum Computation - Gottesman (2010)](https://arxiv.org/abs/0904.2557) - *Error correction techniques for running oracle circuits on noisy hardware.*

- [Synthesis of Quantum Logic Circuits - Shende, Markov & Bullock (2006)](https://doi.org/10.1109/TCAD.2005.855930) - *Tight lower bounds on CNOT gates validating our oracle gate counts.*

- [The Computational Complexity of Linear Optics - Aaronson & Arkhipov (2011)](https://doi.org/10.1145/1993636.1993682) - *Classical intractability of simulating quantum systems.*

- [Universality in Quantum Computation - Deutsch, Barenco & Ekert (1995)](https://doi.org/10.1098/rspa.1995.0065) - *Almost every two-qubit gate is universal, connecting to CNOT-based oracle construction.*

- [Qiskit QuantumCircuit API Documentation](https://docs.quantum.ibm.com/api/qiskit/qiskit.circuit.QuantumCircuit) - *Official reference for building quantum circuits in Qiskit.*

- [Qiskit Aer Simulator Documentation](https://qiskit.github.io/qiskit-aer/stubs/qiskit_aer.AerSimulator.html) - *Reference for verifying oracle correctness via simulation.*

## AI Usage Declaration


Artificial intelligence tools were used in a limited and supportive capacity during the preparation of this work. The following model types were used:

- **ChatGPT (OpenAI GPT-4)**: Used for improving clarity of expression, correcting grammar, and refining written English.
- **Claude (Anthropic Claude 2/3)**: Used for troubleshooting Python issues, providing extra explanation, and assisting with test case creation.

[ChatGPT](https://chatgpt.com/) was occasionally used to assist with improving clarity of expression, correcting grammar, and refining written English. All ideas, analysis, structure, and final content remain my own.

All ideas, analysis, structure, and final content remain my own.

**ChatGPT Example Prompt**

**Me:**

*Before we can really appreciate what makes the Deutsch Jozsa algorithm so remarkable, we first needs to understand what kind of problem it is actually solving.*

*At the centre of it is the Boolean function, which is a mathematical function that take one or more True or False inputs and return a single True or False output. These kind of functions are the building blocks for digital logic and computer circuits. A simple one input Boolean function might always return True no matter what you give it, or it might flip its input and returns False when given True and vice versa.*

**ChatGPT:**

*Before we can appreciate what makes the Deutsch-Jozsa algorithm remarkable, we need to understand the kind of problem it's actually solving.*

*At the heart of it all is the [Boolean function](https://en.wikipedia.org/wiki/Boolean_function), a mathematical function that takes one or more ``True``/``False`` inputs and returns a single ``True``/``False`` output. These functions are the building blocks of digital logic and computer circuits. A simple one-input Boolean function might always return ``True`` no matter what you give it, or it might flip its input, returning ``False`` when given `````True````` and vice versa:*

[Claude](https://claude.ai/new) was consulted in specific instances to help troubleshoot Python related issues when alternative sources such as documentation or online forums did not resolve the problem. Any code produced was carefully reviewed, understood, and adapted where necessary before inclusion. Claude was also used for extra explanation for Python concepts when needed.

Claude was also used in the assistance of creating test cases for problem implementations in the notebook. 

**Claude Example Prompt**

**Me:**

*I understand this function generates either a constant or balanced Boolean function using a lookup table.*

*Can you explain why using a dictionary for the lookup table guarantees that the function is truly balanced when eight inputs are selected?*

**Claude**

*Using a dictionary as a lookup table guarantees correctness because every possible input combination is explicitly mapped to exactly one output value.*

*In your implementation, you first generate all 16 possible input combinations using:*

```python
all_inputs = list(itertools.product([False, True], repeat=4))
```

*This ensures that every possible 4 bit Boolean input exists exactly once in the list.*

*For the balanced case, you then randomly select exactly 8 of those 16 input combinations:*

```python
true_inputs = set(random.sample(all_inputs, 8))
```

*Since random.sample selects without replacement, it guarantees that:*

*Exactly 8 unique inputs are chosen*

*No duplicates can occur*

*Then you construct the lookup table by assigning:*

```python
lookup_table[input_combo] = input_combo in true_inputs
```

**This means:**

*The 8 selected inputs map to True*

*The remaining 8 inputs map to False*

*Because the dictionary contains all 16 possible inputs and exactly 8 are assigned True, the function is mathematically guaranteed to be balanced.*

*The dictionary enforces determinism as well. Once created, every identical input tuple will always return the same output value, which ensures the function behaves consistently like a proper Boolean function.*

While artificial intelligence was used as a helpful tool in the production of my notebook, all work remains reflects my own understanding, research, and ideas.

## Author
*This notebook was written and designed by Fionn McGoldrick*