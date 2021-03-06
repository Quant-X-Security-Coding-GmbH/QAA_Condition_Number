# Condition Number of the Quantum Algebraic Attack on chosen Cryptosystems

*Identifying Security Levels for chosen globally used cryptosystems wrt. the Quantum Algebraic Attack (QAA) by Chen-Gao.*

This repository documents the work in progress on the investigation of the condition numbers of the Macaulay matrices of chosen cryptosystems, which are described in the scientific paper **Quantum Algorithms for Boolean Equation Solving and Quantum Algebraic Attack on Cryptosystems** by Y.-A.Chen, X.-S.Gao, https://arxiv.org/pdf/1712.06239.pdf, 2018. 

The condition numbers will determine the security levels of the related cryptosystems wrt. the **Quantum Algebraic Attack (QAA)**.


## Project 

### Project Slides

* [Slides in English](https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/QAA_condition_number_project_description_EN.pdf)
* [Slides in German](https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/QAA_condition_number_project_description_DE.pdf)


### General Facts about the QAA

* The **QAA** is based on 
	* The HHL algorithm (Quantum Linear Algebra) 
	* Computeralgebra means in order to solve Boolean Multivariate Equation Systems (BMQ).
* To calculate the condition number of the cryptosystems (their security levels respectively), we have to work with Computeralgebra and numerical methods.


### Progress

1) In a first phase, we looked at the cassical notion of a condition number of the QAA on the globally used symmetric Advanced Encryption Standard AES. The classical notion of the condition number takes zero rows and columns of the specific Macaualay matrix into account. For a complex square matrix A which commutes with its own conjugate A* , the condition number is the positive ratio of the maximal and minimal eigenvalues of A. Under these assumptions, the condition number of the QAA on AES equals infinity. 
2) The second (current) phase is the investigation of the condition number of the Macaulay matrix while ignoring zero rows amd columns. This phase consists of the explicit generation of the *reduced Macaulay matrix* of the polynomial system derived from the S-Box and the computation of its condition number by a singular value decomposition (SVD). SVD can be performed on **any** matrix. There are binary implementations and quantum algorithm papers for SVD. Some documentation on our calculations:
	* [singular.md](singular/singular.md) to follow our experiments with the [Computeralgebra System Singular](https://www.singular.uni-kl.de/).
	* [svd.md](singular_value_decomposition/svd.md) for mathematical explanation of the SVD computation.


### Results for AES

1) The key length and the number of rounds have only minor impact on the complexity of the attack. (See N_k and N_r in Proposition 6.1 section 6.1 of the Cen-Gao paper)
2) The complexity of the key schedule function has no impact on the complexity of the QAA, because:

	a) The key and the expanded key are considered key variables in the BMQ.
	b) The derived sub keys are considered state variables in the BMQ.

3) The condition number of the Macaulay matrix of the BMQ for AES equals the condition number of the Macaulay matrix derived from the AES S-Box.
4) The classical condition number of the Macaulay matrix of the S-Box equals infinity.


### Cryptoanalytic Gamechanger QAA

The properties 1. and 2. of the QAA described in the previous section offer considerable advantage over other cryptanalyses, such as Grover's Search algorithm. They also define new criteria for post-quantum cryptography. A cryptosystem offering resilience against the QAA must satisfy at least one of he following criteria:

1) It cannot be reduced to a BMQ
2) If it can be reduced to a BMQ, its QAA Macaulay matrix must have a large condition nummer /kappa.


## Context Computeralgebra

Computeralgebra is the scientific area which concerns itself with mathematical computations without floating point numbers and their implementations. That integrates symbolic computation as well.
Therefore it is the means which materializes mathematical theory into applicable algorithms and programs. 

Cryptography is just one of other many topics which is handled by Computeralgebra researchers.


### Computeralgebra Professionals Group Germany

The Computeralgebra Professionals Group Germany ([Fachgruppe Computeralgebra](https://fachgruppe-computeralgebra.de/fachgruppe/)) is a group of the GI ([Gesellschaft für Informatik](https://gi.de/)). 
Furthermore it is associated to the DMV ([Deutsche Mathematikervereinigung](https://www.mathematik.de/)).


### CAR Article Autumn 2020

We have published a summary of the identified impacts of the QAA in the magazine of the Computeralgebra Expert Group Germany under the title *"Quantum Algebraic Attack"*. 

Our goal is to raise interest in Quantum Computing research in the Computeralgebra community as well as in the industry. The online version will be published in spring 2021.

See our preprint: [CAR article (Computeralgebra Rundbrief October 2020)](computeralgebra/GameChangerComputerAlgebra.pdf).


### Singular Experiments aorund the QAA

Check out [singular.md](singular/singular.md) to follow our experiments with the [Computeralgebra System Singular](https://www.singular.uni-kl.de/).


## Interlude: Important Progress in Quantum Algorithm Design

Important Lecture by I. Chuang on "Grand Unification of Quantum Algorithms" with the goal of enabling the construction of new Quantum Algorithms ( 2020 ): https://www.youtube.com/watch?v=GFRojXdrVXI&t=44s

The 3 main killer Q-algos, search, factoring and simulation, are all on the same structural footing: The quantum singular value transformation algorithm by Gilyen et al.: https://arxiv.org/pdf/1806.01838.pdf

**Remark**: The QAA is not explicitely mentioned, but in the youtube video, I. Chuang  mentions SVD in the context of the HHL algorithm (on which the QAA is built).

Check out [notation.md](notation/notation.md) for mathematical and quantum notation of the described mechanisms and operations.



## Cross References

* eAES mathematical analysis wrt. Grover's Search by Xenia Bogomolec: ([eAES_post-quantum_math_analysis](https://github.com/XeniaGabriela/eAES_post-quantum_math_analysis))

For scientific references used for the calculation of the condition number /kappa see the references in the ([Official Paper](
https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/official_paper/QAA_on_AES_paper.pdf))



## Contributers

* [Dr. Peter Nonnenmann](https://www.linkedin.com/in/peter-dr-nonnenmann-737857a0/): Core Analysis, see [his original paper](https://github.com/XeniaGabriela/QAA_Condition_Nr/tree/master/results_nonnenmann_rump)
* [Xenia Bogomolec](https://www.linkedin.com/in/xenia-bogomolec-532981a6/): Context analysis wrt. Commutative Algebra, Algebraic Geometry, Cryptography and Industry

With the friendly essential support of 
* Prof. Dr. Siegfried Rump (Head of the Institute for for Reliable Computing, TU Harburg)
* Christoph Stockhammer, MathWorks
