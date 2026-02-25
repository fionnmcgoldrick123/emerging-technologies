# Emerging Technologies Assessment Classical and Quantum Algorithms

## Overview

This repository contains a comprehensive exploration of classical and quantum algorithms, focusing on the [Deutsch-Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa) and its predecessor, [Deutsch's algorithm](https://quantum.cloud.ibm.com/learning/en/courses/fundamentals-of-quantum-algorithms/quantum-query-algorithms/deutsch-algorithm). The [problems.ipynb](problems.ipynb) notebook demonstrates the fundamental differences between classical and quantum approaches to determining whether [Boolean functions](https://en.wikipedia.org/wiki/Boolean_function) are constant or balanced, showcasing one of the earliest proven quantum computational advantages.

The notebook progresses through five interconnected problems that build understanding from classical function generation to full quantum algorithm implementation. Beginning with Python-based classical solutions, it transitions to quantum circuit design using [Qiskit](https://www.ibm.com/quantum/qiskit), ultimately demonstrating how quantum computers can solve certain problems exponentially faster than their classical counterparts. Each problem includes detailed theoretical background, implementation code, comprehensive testing, and analysis of efficiency and limitations.

## Assessment Brief

This repository was created as part of the Emerging Technologies module assessment for Summer 2025/26. The primary objective is to demonstrate understanding of both classical and quantum computing concepts through the completion of five interconnected problems presented in the [problems.ipynb](problems.ipynb) notebook.

**Project Scope**: The assessment requires implementing and analyzing algorithms that determine properties of Boolean functions, progressing from classical algorithmic approaches to quantum computing solutions. This includes developing random function generators, classical testing algorithms, quantum oracles, and implementations of both Deutsch's and Deutsch-Jozsa algorithms.

**Development Approach**: This project has been developed incrementally with regular commits throughout the semester, ensuring proper version control practices and demonstrating consistent progress. All code is designed to be reproducible and executable by computing professionals familiar with Python and Jupyter notebooks, with comprehensive setup instructions provided below.

**Target Audience**: This repository is intended for informed computing professionals, such as potential employers or academic reviewers, who have a strong foundation in computer science but may not be specialists in quantum computing. All necessary dependencies, setup procedures, and theoretical background are documented to enable seamless reproduction of results.



## Repository Contents

- **[problems.ipynb](problems.ipynb)**: The main Jupyter notebook containing all five problems exploring classical and quantum algorithms, with detailed implementations, explanations, tests, and analysis. This notebook progresses from classical Boolean function generation through the implementation of Deutsch's and Deutsch-Jozsa algorithms.

- **[README.md](README.md)**: This file, provides an overview of the project, setup instructions, solution summaries, and references.

- **[requirements.txt](requirements.txt)**: Lists all Python package dependencies required to run the notebook, including Qiskit, Jupyter, NumPy, and Matplotlib.

- **[.gitignore](.gitignore)**: Specifies which files and directories Git should ignore (e.g., virtual environments, Python cache files).

## Repository Structure

The repository follows a simple, flat structure for ease of navigation:

```
emerging-technologies/
├── problems.ipynb          # Main Jupyter notebook with all five problems
├── README.md               # Project overview and documentation
├── requirements.txt        # Python package dependencies
├── .gitignore             # Git ignore rules
└── .venv/                 # Virtual environment (not tracked in Git)
```

This minimal structure ensures all essential files are easily accessible from the repository root, following best practices for academic and professional Python projects. 

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


All implementations have been tested and verified using Qiskit's quantum simulators. Key findings include:

- **Classical Baseline**: For 4-input Boolean functions, classical algorithms require up to 9 queries (2^(n-1) + 1) to deterministically classify functions as constant or balanced.

- **Quantum Advantage**: Both Deutsch's algorithm and the Deutsch-Jozsa algorithm achieve 100% accuracy with only a single oracle query, demonstrating provable quantum computational advantage.

- **Scalability**: While the classical query complexity grows exponentially with input size, the quantum approach maintains constant (single) query complexity, showcasing one of quantum computing's fundamental strengths.

- **Circuit Verification**: All quantum oracles and algorithms have been validated through comprehensive testing, with circuit diagrams and measurement statistics included in the notebook.

Detailed results, including quantum circuit visualizations, measurement histograms, and complexity analyses, are available in [problems.ipynb](problems.ipynb).
### Problem 3: Quantum Oracles

Creates quantum oracles for all four single-input Boolean functions (f₀, f₁, f₂, f₃) using Qiskit. Each oracle implements the reversible transformation |x⟩|y⟩ → |x⟩|y ⊕ f(x)⟩ using quantum gates (X, CNOT). The implementation demonstrates key quantum computing principles including reversibility, the XOR trick for preserving quantum information, and how classical functions are encoded as unitary quantum operations. All oracles are verified through comprehensive testing on quantum simulators.

### Problem 4: Deutsch's Algorithm with Qiskit

Implements Deutsch's algorithm, which solves the constant vs. balanced problem for single-input functions with just one oracle query—a 50% reduction from the classical requirement of two queries. The quantum circuit uses superposition and quantum interference to extract global properties of the function. By preparing the output qubit in the |−⟩ state and the input qubit in the |+⟩ state, the algorithm exploits phase kickback to encode the function's type in the final measurement outcome.

### Problem 5: Scaling to the Deutsch–Jozsa Algorithm

Extends Deutsch's algorithm to handle multi-input functions, specifically the 4-input Boolean functions from Problem 1. The Deutsch-Jozsa algorithm maintains the single-query advantage even as the input size grows, representing an exponential speedup over classical approaches (1 query vs. 9 queries for 4 inputs). The implementation demonstrates how oracles for complex Boolean functions are constructed and how the quantum Fourier transform-like interference pattern enables efficient function classification on quantum hardware.

## Results

## References

- [Rapid Solution of Problems by Quantum Computation - Deutsch & Jozsa (1992)](https://doi.org/10.1098/rspa.1992.0167) - *Original Deutsch-Jozsa algorithm paper defining constant vs balanced classification.*

- [Quantum Theory, the Church-Turing Principle and the Universal Quantum Computer - Deutsch (1985)](https://doi.org/10.1098/rspa.1985.0070) - *Foundational paper proposing quantum computation and the single-bit problem.*

- [Quantum Computing Since Democritus - Aaronson (2013)](https://www.cambridge.org/core/books/quantum-computing-since-democritus/F77C0E5B2E37A0B05BDE0835E582E41E) - *Discusses query complexity and oracle separations for Deutsch-Jozsa.*

- [Quantum Complexity Theory - Bernstein & Vazirani (1997)](https://doi.org/10.1137/S0097539796300921) - *Extends Deutsch-Jozsa to prove broader quantum-classical separations.*

- [Quantum Computing in the NISQ Era and Beyond - Preskill (2018)](https://doi.org/10.22331/q-2018-08-06-79) - *Contextualizes idealized algorithmic advantages against practical hardware constraints.*

- [The Art of Computer Programming, Volume 2 - Knuth (1997)](https://www-cs-faculty.stanford.edu/~knuth/taocp.html) - *Covers pseudorandom number generation used in Python's `random` module.*

- [Models of Computation - Savage (1998)](https://doi.org/10.1007/978-1-4612-0575-8) - *Discusses exponential blowup in truth table representations of Boolean functions.*

- [Structure and Interpretation of Computer Programs - Abelson & Sussman (1996)](https://mitpress.mit.edu/9780262510875/) - *Functions as first-class objects, relevant to our callable function design.*

- [Discrete Mathematics and Its Applications - Rosen (2019)](https://www.mheducation.com/highered/product/discrete-mathematics-applications-rosen/M9781259676512.html) - *Boolean algebra foundations and combinatorial basis for balanced function counting.*

- [Quantum Computing for the Very Curious - Matuschak & Nielsen (2019)](https://quantum.country/qcvc) - *Interactive essay on quantum superposition and interference.*

- [Quantum Algorithm Implementations for Beginners - Coles et al. (2022)](https://doi.org/10.1145/3517340) - *Practical Deutsch-Jozsa implementation with code examples. [arXiv:1804.03719](https://arxiv.org/abs/1804.03719).*

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

Artificial intelligence tools were used in a limited and supportive capacity during the preparation of this work. 

[ChatGPT](https://chatgpt.com/) was occasionally used to assist with improving clarity of expression, correcting grammar, and refining written English. All ideas, analysis, structure, and final content remain my own.

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