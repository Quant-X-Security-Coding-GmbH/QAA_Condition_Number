# Condition Number of the Quantum Algebraic Attack on chosen Cryptosystems

On the condition number of the Qantum Algebraic Attack (QAA) by Chen-Gao for chosen cryptosystems

## Objective

This repository documents the work in progress on the investigation of the condition number of the scientific paper
**Quantum Algorithms for Boolean Equation Solving and Quantum Algebraic Attack on Cryptosystems**
by Y.-A.Chen, X.-S.Gao, https://arxiv.org/abs/1712.06239}, 2018.


## History

* In a first step, we looked at the cassical notion of a condition number of the QAA on the globally used symmetric Advanced Encryption Standard AES. 
* The second phase will consist of the explicit generation of the reduced Macaulay matrix of the polynomial system derived from the S-Box and the actual computation of its condition number.


### Facts about QAA on AES

* The QAA on AES is based on solving Boolean Multivariate Equation System (BMQ). 
* The condition number of the QAA on AES, equals the condition number of the Macaulay matrix of the BMQ for AES.
* The key and the expanded key are considered as key variables in the BMQ.
* The derived sub keys are considered as state variables in the BMQ.
* Due to the last two points, the key schedule function of AES has no explicit impact on the condition number of AES. 
* The key length and the number of rounds only have only minor impact on the complexity of the attack. (See N_k and N_r in Proposition 6.1 section 6.1 of the Cen-Gao paper)


### Results for AES

* The condition number of the Macaulay matrix of the BMQ for AES equals the condition number of the Macaulay matrix derived from the AES S-Box.
* The classical condition number of the Macaulay matrix of the S-Box equals infinity



## Cross References

* eAES mathematical analysis wrt. Grover's Search by Xenia Bogomolec: ([eAES_post-quantum_math_analysis](https://github.com/XeniaGabriela/eAES_post-quantum_math_analysis))

Scientific references used for the computation of the condition number see the references in the ([Official Paper](
https://github.com/XeniaGabriela/QAA_Condition_Nr/blob/master/official_paper/QAA_on_AES_paper.pdf)) on the Complexity of the Quantum Algebraic Attack on AES.


## Contributers
* [Dr. Peter Nonnenmann](https://www.linkedin.com/in/peter-dr-nonnenmann-737857a0/): Core Analysis, see [his original paper](https://github.com/XeniaGabriela/QAA_Condition_Nr/tree/master/results_nonnenmann_rump)
* [Xenia Bogomolec](https://www.linkedin.com/in/xenia-bogomolec-532981a6/): Context analysis wrt. Commutative Algebra, Algebraic Geometry, Cryptography and Industry

With the friendly essential support of 
* Prof. Dr. Siegfried Rump (Head of the Institute for for Reliable Computing, TU Harburg)
* Christoph Stockhammer, MathWorks