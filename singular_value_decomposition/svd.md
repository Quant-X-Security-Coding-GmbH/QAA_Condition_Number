# Singular Value Decomposition

SVD can be performed on **any** matrix. There are binary implementations and quantum algorithm papers for SVD. We need the SVD to compute the condition number \kappa of the reduced Macaulay matrices of the chosen cryptosystems. With \kappa, we can then compute the security levels of the cryptosystems wrt. the Quantum Algebraic Attack.



## SVD-Algorithm (Singular Value Decomposition)

For starting experiments on SVD calculations. In pseudo code:

Algorithm.SVD

Input: (m,n)-Matrix A
Output: SVD  A = U.S.V^T  ,
where U (m,m) consists of the left, and V (n,n) of the right singular vectors, and
S (m,n) is diagonal, S=diag(s1,...,sp) , the s_i are the singular values , p := min(m,n), r is the rank of A .

1. If m > n , calculate A^T.A , Else , calculate A.A^T .
2. Let m > n , calculate the eigenvalues la_i of the hermitian matrix A^T.A .
   The singular values s_i are the square roots( la_i ) .
   r is equal to the number of non-zero singular values.
3. Calculate an orthonormal Eigenbasis of A^T.A , ( v1,...,vn ) .
   The latter is equal to V = ( v1,...,vn ), the v_i are the columns of V .
4. As for U :

              FOR  i = 1 to r  DO
              u_i := (1/s_i) Av_i 
   
              FOR  i = r+1 to m  DO
              The columnvectors (u_r+1,...,u_m) of U are an orthonormal basis of Ker(A^T),
              which can be calculated by calling the Algorithm.BASIS-OF-KERNEL below.
END.SVD    


## SVD with Python

* ["AskPython" (numpy and scikit-learn)](https://www.askpython.com/python/examples/singular-value-decomposition)
* ["Towards Data Science" onnline example](https://towardsdatascience.com/singular-value-decomposition-example-in-python-dab2507d85a0)
* [numpy.linalg.svd module docs](https://numpy.org/doc/stable/reference/generated/numpy.linalg.svd.html)


## Killer App Google's PageRank Algorithm

As a major application of Matrix Factorizations/Diagonalization, check out this: https://projecteuclid.org/download/pdf_1/euclid.im/1109190965
See also on Github XeniaGabriela/dwave.

The typical size of the matrix in Google's PageRank Algorithm is 4.3 billion by 4.3 billion, and they are willing to do a few hundred iterations.

In the linear systems formulation, as opposed to the original Markov chain treatment of Brin & Page, the matrix

    ( I  - alpha.P' )
    
    where I is the identity matrix, alpha is a real parameter, and P' some matrix,
    
plays a central role. Its condition number is known:

     k( I - alpha.P' )  =  ( 1 + alpha ) / ( 1 - alpha ).
     
Brin & Page's original choice was  alpha = 0.85,
alpha = 1  gives

     k ( I -   1 .P' )  =  2 / 0  =  infinity.
