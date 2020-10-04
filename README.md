# Condition Number of the Quantum Algebraic Attack on chosen Cryptosystems

*Fundamental Research as Open Source Project between Science and Industry*

Identifying Security Levels for chosen globally used cryptosystems wrt. the Quantum Algebraic Attack (QAA) by Chen-Gao.


## Objective

This repository documents the work in progress on the investigation of the condition number of the scientific paper
**Quantum Algorithms for Boolean Equation Solving and Quantum Algebraic Attack on Cryptosystems**
by Y.-A.Chen, X.-S.Gao, https://arxiv.org/pdf/1712.06239.pdf, 2018.


## Project Description

* [Slides in English](https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/QAA_condition_number_project_description_EN.pdf)
* [Slides in German](https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/QAA_condition_number_project_description_DE.pdf)


## Progress

* In a first phase, we looked at the cassical notion of a condition number of the QAA on the globally used symmetric Advanced Encryption Standard AES. Under these assumptions, the condition number of the QAA on AES equals infinity. 
* The second (current) phase is the investigation of the condition number of the Macaulay matrix while ignoring zero rows amd columns. This pahse consists of the explicit generation of the reduced Macaulay matrix of the polynomial system derived from the S-Box and the actual computation of its condition number.

Check out [singular.md](singular/singular.md) to follow our experiments with the [Computeralgebra System Singular](https://www.singular.uni-kl.de/).


### Facts about the QAA

* The QAA on cryptosystems is based on solving Boolean Multivariate Equation System (BMQ). 

#### Facts about the QAA on AES

The key length and the number of rounds only have only minor impact on the complexity of the attack. (See N_k and N_r in Proposition 6.1 section 6.1 of the Cen-Gao paper)

The complexity of the key schedule function has no impact on the complexity of the QAA, because:

* The key and the expanded key are considered as key variables in the BMQ.
* The derived sub keys are considered as state variables in the BMQ.

This special property of the QAA offers a serious advantage over other cryptanalyses, such as Grover's Search algorithm. It also defines new criteria for post-quantum cryptography. A cryptosystem offering resilience against the QAA must satisfy at least one of he following criteria:

1) It cannot be reduced to a BMQ
2) If it can be reduced to a BMQ, its QAA Macaulay matrix must have a large condition nummer /kappa.


### Results for AES

* The condition number of the Macaulay matrix of the BMQ for AES equals the condition number of the Macaulay matrix derived from the AES S-Box.
* The classical condition number of the Macaulay matrix of the S-Box equals infinity



## Cross References

* eAES mathematical analysis wrt. Grover's Search by Xenia Bogomolec: ([eAES_post-quantum_math_analysis](https://github.com/XeniaGabriela/eAES_post-quantum_math_analysis))

For scientific references used for the computation of the condition number see the references in the ([Official Paper](
https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/official_paper/QAA_on_AES_paper.pdf))


## Contributers
* [Dr. Peter Nonnenmann](https://www.linkedin.com/in/peter-dr-nonnenmann-737857a0/): Core Analysis, see [his original paper](https://github.com/XeniaGabriela/QAA_Condition_Nr/tree/master/results_nonnenmann_rump)
* [Xenia Bogomolec](https://www.linkedin.com/in/xenia-bogomolec-532981a6/): Context analysis wrt. Commutative Algebra, Algebraic Geometry, Cryptography and Industry

With the friendly essential support of 
* Prof. Dr. Siegfried Rump (Head of the Institute for for Reliable Computing, TU Harburg)
* Christoph Stockhammer, MathWorks