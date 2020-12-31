# Notation

## Summary

* Bra: < a |  ==> a row vector
* Ket: | b >  ==> a column vector
* < a | b > is the scalar product of a and b, a complex number
* | b >  < a | is a matrix ([see this example](https://www.matheretter.de/wiki/spaltenvektor-mal-zeilenvektor))
*  |a> |b> := |a> tensor |b>  :=  |a b>  is the tensor product of two vectors or matrices (see here: https://en.wikipedia.org/wiki/Kronecker_product)

##  Dirac-Ket-Notation and Matrix-Algebra

Consider the 1-qubit space C^2: 

A typical element is a 2-column vector  v = ( z1 , z2 )^T, z_i are complex numbers, T denotes the Transpose.

In Dirac notation this written  v = |v>  =  a ket-state.

The DUAL SPACE  (C^2)* is defined as the vector space of linear forms  f: C^2 --> C . In Dirac notation this is written  f = < v | =  a bra-state.

The linear forms can be identified with 2-row vectors:                 
< v |  = ( z1* , z2* ), where z_i* = the complex-conjugate ( z_i ).


The Dirac operations < a | b > , < a | b | c > etc. are defined by various MATRIX MULTIPLICATIONS.

A matrix A has a TYPE (n,m) = (# of rows , # of columns).
Then the type of a product A.B is defined as: (n,m).(m,p)  =  (n,p)

So < u | v > is the scalar product:

* < u | = 2-row vector with type: (1,2), multiplied with 
* | v > = 2-column vector with type: (2,1) 

and < u | v > has type (1,2).(2,1) = (1,1) = scalar (in this case a complex number).

There is a nice example in the section "Multiplying bras and kets" in Steven Holzner's [How to Use Kets, the Hermitian Conjugate, and Bra-ket Notation](https://www.dummies.com/education/science/quantum-physics/how-to-use-kets-the-hermitian-conjugate-and-bra-ket-notation/).

< u | A | v > is a triple product with u, v as above and A is a (2,2)-matrix (here a 1-qubit gate).

The types are: (1,2).(2,2).(2,1) = (1,2).(2,1) = (1,1), a scalar, 
where the matrix product is associative, but not commutative in general.


## Physical Meaning of both Types of Product

Let |v> be the starting state of a quantum system before a measurement is done, and |u> the ending state
after the measurement is carried out. Then | <u|v> |^2  is the probability that, starting in |v>, we end up
in |u> after the measurement.

In Quantum Theory, STATES are modelled by ket-vectors in a Hilbert space, as described above.
OBSERVABLES are modelled by Hermitian operators or matrices A , that are defined by

< u | A | v >  =  < Au | v >   for all  u,v .

From this follows that  < v | A | v > =: <A>_v   is a real number for all  v.

There is an Axiom in Quantum Theory, that <A>_v is the EXPECTED VALUE of observing A repeatedly on the same state v .      
  
