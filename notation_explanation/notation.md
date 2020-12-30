# Notation

## Summary

* Bra: < a |  ==> a row vector
* Ket: | b >  ==> a column vector
* < a | b > is the scalar product of a and b, a complex number
* | b >  < a | is a matrix


####  Dirac-Ket-Notation and Matrix-Algebra

Consider the 1-qubit space C^2: 

A typical element is a 2-column vector  v = ( z1 , z2 )^T, z_i are complex numbers, T denotes the Transpose.

In Dirac notation this written  v = |v>  =  a ket-state.

The DUAL SPACE  (C^2)* is defined as the vector space of linear forms  f: C^2 --> C . In Dirac notation this is written  f = < v | =  a bra-state.

The linear forms can be identified with 2-row vectors :                 
< v |  = ( z1* , z2* ), where z_i* = the complex-conjugate ( z_i ) .


The Dirac operations < a|b > , < a|b|c > etc. are defined by various MATRIX MULTIPLICATIONS.

A matrix A has a TYPE (n,m) = ( # of rows , # of columns ).
Then the type of a product A.B is defined as: (n,m).(m,p)  =  (n,p)

So <u|v> is the scalar product: < u | = 2-row vector with type : (1,2)   multiplied with | v > = 2-column vector with type: (2,1), and <u|v> has type (1,2).(2,1) = (1,1) = scalar (a complex number).

< u|A|v > is a triple product with u, v as above and A is a (2,2)-matrix = 1 qubit gate.

The types are: (1,2).(2,2).(2,1) = (1,2).(2,1) = (1,1) = scalar,
where the matrix product is associative, but not commutative in general.

I will soon write more about the physical meaning of both types of product.                                                                             
                                                                            