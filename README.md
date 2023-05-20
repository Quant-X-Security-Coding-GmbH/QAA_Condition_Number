# Condition Number of the Quantum Algebraic Attack on chosen Cryptosystems

*Identifying Security Levels for chosen globally used cryptosystems wrt. the Quantum Algebraic Attack (QAA) by Chen-Gao.*

This repository documents the work in progress on the investigation of the condition numbers of the Macaulay matrices of chosen cryptosystems, which are described in the scientific paper **Quantum Algorithms for Boolean Equation Solving and Quantum Algebraic Attack on Cryptosystems** by Y.-A.Chen, X.-S.Gao, https://arxiv.org/pdf/1712.06239.pdf, 2018. 

The condition numbers will determine the security levels of the related cryptosystems wrt. the **Quantum Algebraic Attack (QAA)**.


## Project 

### Notation

Check out [notation.md](https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/blob/main/notation_explanation/notation.md) for mathematical and quantum notation of the described mechanisms and operations.

### Project Slides

* [Slides in English](https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/blob/main/QAA_condition_number_project_description_EN.pdf)
* [Computeralgebra Conference Presentation](https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/blob/main/QAA_Talk%20PNo.pdf)

### General Facts about the QAA

* The **QAA** is based on 
	* The HHL algorithm (Quantum Linear Algebra) 
	* Computeralgebra means in order to solve Boolean Multivariate Equation Systems (BMQ).
* To calculate the condition number of the cryptosystems (their security levels respectively), we have to work with Computeralgebra and numerical methods.


### Progress

1) In a first phase, we looked at the classical notion of a condition number of the QAA on the globally used symmetric Advanced Encryption Standard AES. The classical notion of the condition number takes zero rows and columns of the specific Macaualay matrix into account. For a complex square matrix A which commutes with its own conjugate A* , the condition number is the positive ratio of the maximal and minimal eigenvalues of A. Under these assumptions, the condition number of the QAA on AES equals infinity. 
2) The second phase was the investigation of the condition number of the Macaulay matrix while ignoring zero rows amd columns. This phase consists of the explicit generation of the *reduced Macaulay matrix* of the polynomial system derived from the S-Box and the computation of its condition number by a singular value decomposition (SVD). SVD can be performed on **any** matrix. There are binary implementations and quantum algorithm papers for SVD. Some documentation on our calculations:
	* [singular.md](https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/blob/main/computeralgebra/singular/singular.md) to follow our experiments with the [Computeralgebra System Singular](https://www.singular.uni-kl.de/).
	* [svd.md](singular_value_decomposition/svd.md) for mathematical explanation of the SVD computation.

3) By feedback from particpants of the [Industrial Computeralgebra Conference with Focus Cryptography](https://fachgruppe-computeralgebra.de/industrial-computeralgebra-conference-with-focus-cryptography/), the security levels can be estimated by a lower bound. See [Limitations of the Macaulay matrix approach for using the HHL algorithm to solve multivariate polynomial systems](https://indico.physik.uni-muenchen.de/event/84/attachments/248/553/S2C.Li.slides.pdf). Chen/Gao’s algorithm is exponential in the Hamming weight (number of one’s) of the solution (the secret key + the expanded key + derived sub keys). A randomly generated symmetric secret key should have about equally many zero’s as one’s. Under this assumption, the Hamming weight of the solution is about half the size of the solution vector. The structure of the AES Macaulay matrix implies a far lower Hamming weight though. It is our next goal to compute the Hamming weight of this matrix. After this we will continue  the research about a new method to compute the condition number of the huge matrix.

One of the above mentioned authors, Sean Hallgren, presents here
[An efficient Quantum Algorithm for Lattice Problems achieving subexponential approximation factor.](https://www.youtube.com/watch?v=K5Apl_qCnDA) , rendering some of these Post-Quantum ciphers quantum-attackable.


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


### Industrial Computeralgebra Conference with Focus Cryptography September 2021

We received some new insights from other participants of the conference: The secruity levels can be estimated by a lower bound. See [Limitations of the Macaulay matrix approach for using the HHL algorithm to solve multivariate polynomial systems](https://indico.physik.uni-muenchen.de/event/84/attachments/248/553/S2C.Li.slides.pdf). 

* [Conference](https://fachgruppe-computeralgebra.de/industrial-computeralgebra-conference-with-focus-cryptography/)
* [Speakers](https://fachgruppe-computeralgebra.de/industrial-conference-talks/)


### CAR Article Autumn 2020

We have published a summary of the identified impacts of the QAA in the magazine of the Computeralgebra Expert Group Germany under the title *"Quantum Algebraic Attack"*. 

Our goal is to raise interest in Quantum Computing research in the Computeralgebra community as well as in the industry. The online version will be published in spring 2021.

See our preprint: [CAR article (Computeralgebra Rundbrief October 2020)](computeralgebra/GameChangerComputerAlgebra.pdf).


### Singular Experiments around the QAA

Check out [singular.md](https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/blob/main/computeralgebra/singular/singular.md) to follow our experiments with the [Computeralgebra System Singular](https://www.singular.uni-kl.de/).



## Cross References


### Condition Number

For scientific references used for the calculation of the condition number /kappa see the references in the ([Official Paper](
https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/blob/main/official_paper/QAA_on_AES_paper.pdf))


### Quantum Singular Value Transformation and HHL

Lecture by I. Chuang on ["Grand Unification of Quantum Algorithms"](https://www.youtube.com/watch?v=GFRojXdrVXI&t=44s) with the goal of enabling the construction of new Quantum Algorithms (2020)

The 3 main Quantum-algorithms, search, factoring and simulation, are all on the same structural footing, which is the the [quantum singular value transformation algorithm by Gilyen et al.](https://arxiv.org/pdf/1806.01838.pdf) The QAA is not explicitely addressed, but I. Chuang  mentions SVD in the context of the HHL algorithm (on which the QAA is built).


### Grover's Search

eAES mathematical analysis wrt. Grover's Search by Xenia Bogomolec: ([eAES_post-quantum_math_analysis](https://github.com/XeniaGabriela/eAES_post-quantum_math_analysis))


## Contributers

* [Xenia Bogomolec](https://www.linkedin.com/in/xenia-bogomolec-532981a6/): Context analysis wrt. Commutative Algebra, Algebraic Geometry, Cryptography and Industry, Singular examples
* [Dr. Peter Nonnenmann](https://www.linkedin.com/in/peter-dr-nonnenmann-737857a0/): Quantum theoretical analysis, see [his original paper](https://github.com/Quant-X-Security-Coding-GmbH/QAA_Condition_Number/tree/main/results_nonnenmann_rump)

With the friendly essential support of 
* Prof. Dr. Siegfried Rump (Head of the Institute for for Reliable Computing, TU Harburg)
* Christoph Stockhammer, MathWorks
