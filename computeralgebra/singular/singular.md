# Computing the Condition Number with Singular

We chose the [Computeralgebra System Singular](https://www.singular.uni-kl.de/) for our first tests to create the Macaulay matrix for the QAA on AES. 


## Polynomials of the AES S-Box

First we created a Singular compatible notation of the 39 Boolean quadratic polynomials for the AES S-Box can be found in the 8 Appendix of original paper: [Boolean quadratic polynomials of the AES S-Box for Singular](AES_polys_Chen_Gao_vars)



## Ring Declaration and Monomial Orderings

The purpose of a monomial ordering is to have a well defined structure for each pair of monomials w.r.t. the relation "greater than". With many variables in a polynomial ring, this structure is not naturally achieved. E. g. in *R(x,y)*, how can we decide if *x²y² > x³y* or the other way around? Monomial orderings are essential in Computeralgebra for any computation. 

We are handling quite [long quadratic polynomials]((AES_polys_Chen_Gao_vars)) here. You can find a purely abstract definition of monomial orderings on [B.2.3 Global orderings](https://www.singular.uni-kl.de/Manual/4-3-2/sing_978.htm#SEC1035). We want to make the impact to the related computations touchable by printing the first polynomial *f_1* in a few chosen monomial orderings.


### Degree Reverse Lexicographical Ordering with Descending Indexes

We identified the ring declaration in Singular corresponding to the monomial ordering of the Boolean quadratic polynomials in the original paper by testing the monomial ordering of the polynomial *f_1(x_7,..., x_0, y_7,..., y_0):*

1) Define the ring of polynomials:

`
ring r=complex,(x(7..0),y(7..0)),dp;
`, where

* *complex* stands for complex coefficients, 
* *x(7..0)* for the variables x_7, ..., x_0 
* *y(7..0)* for the variables y_7, ..., y_0 
* *dp* stands for **degree reverse lexicographical ordering**, according to the original paper with variable index ordering *x_7 > ... x_0 > y_7 > ... > y_0 > 1*.


2) Define the polynomial *f_1*:
```
poly f_1=x(5)*x(7)+x(5)*x(6)+x(3)*x(7)+x(3)*x(6)+x(2)*x(4)+x(1)*x(7)+x(1)*x(6)+x(1)*x(5)+x(1)*x(3)+x(1)*x(2)+x(0)*x(7)+x(0)*x(3)+x(0)*x(2)+x(6)*y(7)+x(7)*y(6)+x(6)*y(6)+x(7)*y(5)+x(5)*y(5)+x(7)*y(4)+x(1)*y(4)+x(2)*y(3)+x(0)*y(3)+x(6)*y(2)+x(4)*y(2)+x(3)*y(2)+x(0)*y(2)+x(4)*y(0)+x(2)*y(0)+x(7)+x(5)+x(3)+y(7)+y(2)+y(0)+1;
``` 

3) Print the polynomial *f_1* in the monomial ordering *dp*:

```
poly f_1;
```
and the output is
```
x(7)*x(5)+x(6)*x(5)+x(7)*x(3)+x(6)*x(3)+x(4)*x(2)+x(7)*x(1)+x(6)*x(1)+x(5)*x(1)+x(3)*x(1)+x(2)*x(1)+x(7)*x(0)+x(3)*x(0)+x(2)*x(0)+x(6)*y(7)+x(7)*y(6)+x(6)*y(6)+x(7)*y(5)+x(5)*y(5)+x(7)*y(4)+x(1)*y(4)+x(2)*y(3)+x(0)*y(3)+x(6)*y(2)+x(4)*y(2)+x(3)*y(2)+x(0)*y(2)+x(4)*y(0)+x(2)*y(0)+x(7)+x(5)+x(3)+y(7)+y(2)+y(0)+1
```

The descending order of variable indexes lead to an order of monomials in the polynomial *f_1* which matches the corresponding polynomial in the original paper (ignoring the order of factors in monomials). So they are working in the polynomial ring with 16 variables over the complex numbers and **the degree reverse lexicographical ordering**.

With a consdieration of the polynomial from the left to the right we see that the lead monomial is the quadratic monomial with the highest index in *x* and the highest index sum followed by the quadratic monomial in *x* with the second highest index sum. However, `x(4)*x(2)` > `x(7)*x(1)` but `x(4)*x(2)`  has a lower index sum than `x(7)*x(1)`. So, we realize that the **degree reverse lexicographical ordering** is defined from the right to the left: 

1. The degree of a monomial has the highest impact on the order of a monomial (1 with degree 0 is smaller than any monomial of degree 1, which are smaller than any monomials of degree 2)
2. Within the first ordered groups of monomials with the same degree, the index of the lowest variable determines the order, e. g. y(0) < y(2), y(7) < x(3) < x(7), `x(6)*y(2)` < `x(0)*y(3)` and `x(7)*x(1)` < `x(4)*x(2)`. 


### Degree Reverse Lexicographical Ordering with Ascending Indexes

An ascending order *x_0 > ... x_7 > y_0 > ... > y_7 > 1* of variable indexes lead to a deviation of the polynomial f_1 from the corresponding polynomial in the original paper:

```
ring r2=complex,(x(0..7),y(0..7)),dp; 
```
Define the polynomial *f_1* in the new ring r2 and print it:
```
poly f_1=x(5)*x(7)+x(5)*x(6)+x(3)*x(7)+x(3)*x(6)+x(2)*x(4)+x(1)*x(7)+x(1)*x(6)+x(1)*x(5)+x(1)*x(3)+x(1)*x(2)+x(0)*x(7)+x(0)*x(3)+x(0)*x(2)+x(6)*y(7)+x(7)*y(6)+x(6)*y(6)+x(7)*y(5)+x(5)*y(5)+x(7)*y(4)+x(1)*y(4)+x(2)*y(3)+x(0)*y(3)+x(6)*y(2)+x(4)*y(2)+x(3)*y(2)+x(0)*y(2)+x(4)*y(0)+x(2)*y(0)+x(7)+x(5)+x(3)+y(7)+y(2)+y(0)+1;
poly f_1;
x(0)*x(2)+x(1)*x(2)+x(0)*x(3)+x(1)*x(3)+x(2)*x(4)+x(1)*x(5)+x(1)*x(6)+x(3)*x(6)+x(5)*x(6)+x(0)*x(7)+x(1)*x(7)+x(3)*x(7)+x(5)*x(7)+x(2)*y(0)+x(4)*y(0)+x(0)*y(2)+x(3)*y(2)+x(4)*y(2)+x(6)*y(2)+x(0)*y(3)+x(2)*y(3)+x(1)*y(4)+x(7)*y(4)+x(5)*y(5)+x(7)*y(5)+x(6)*y(6)+x(7)*y(6)+x(6)*y(7)+x(3)+x(5)+x(7)+y(0)+y(2)+y(7)+1
```
The lead monomial is now the quadratic monomial in *x* with the lowest index sum followed by the quadratic monomial in *x* with the second lowest index sum. But here again we find this pattern broken by `x(5)*x(6)` with an indes sum of 11 being greater than `x(0)*x(7)` with an index sum of 7. As a high index means that the variable is low we can simply substitute a low variable index by a high high variable idex in the reasoning of the previous section to make it applcable for the **degree reverse lexicographical ordering with ascending indexes**.

Demonstrating the impact of ascending and descending indexes was merely a little fun experiment. Now we will print *f_1* in various global monomial orderings:


### Lexicographical Ordering

Define the ring r3 with lexicographical ordering lp:
```
ring r3=complex,(x(7..0),y(7..0)),lp;
```
Define the polynomial *f_1* in the new ring r and print it:
```
poly f_1=x(5)*x(7)+x(5)*x(6)+x(3)*x(7)+x(3)*x(6)+x(2)*x(4)+x(1)*x(7)+x(1)*x(6)+x(1)*x(5)+x(1)*x(3)+x(1)*x(2)+x(0)*x(7)+x(0)*x(3)+x(0)*x(2)+x(6)*y(7)+x(7)*y(6)+x(6)*y(6)+x(7)*y(5)+x(5)*y(5)+x(7)*y(4)+x(1)*y(4)+x(2)*y(3)+x(0)*y(3)+x(6)*y(2)+x(4)*y(2)+x(3)*y(2)+x(0)*y(2)+x(4)*y(0)+x(2)*y(0)+x(7)+x(5)+x(3)+y(7)+y(2)+y(0)+1;
poly f_1;
x(7)*x(5)+x(7)*x(3)+x(7)*x(1)+x(7)*x(0)+x(7)*y(6)+x(7)*y(5)+x(7)*y(4)+x(7)+x(6)*x(5)+x(6)*x(3)+x(6)*x(1)+x(6)*y(7)+x(6)*y(6)+x(6)*y(2)+x(5)*x(1)+x(5)*y(5)+x(5)+x(4)*x(2)+x(4)*y(2)+x(4)*y(0)+x(3)*x(1)+x(3)*x(0)+x(3)*y(2)+x(3)+x(2)*x(1)+x(2)*x(0)+x(2)*y(3)+x(2)*y(0)+x(1)*y(4)+x(0)*y(3)+x(0)*y(2)+y(7)+y(2)+y(0)+1
```
The **lexicographical ordering** is defined from the left to the right: 

1. The monomials are ordered by the highest variable factor: First we have all monomials with x(7) as a factor, then all monomials with x(6), then all monomials with x(5), etc.
2. Within these groups of `x(7)* ...`, `x(6)* ...`, ..., `x(0)* ...`, ..., `1* ...`, the order of the monomials is determined by the order of the second factor. E. g., `x(7)* x(0)` > `x(7)* y(6)` and `x(2)* x(0)` > `x(2)* y(3)`.
3. The degree of the monomials has no direct impact on the ordering E. g. `x(7)` > `x(6)*x(5)`.


### Reverse Lexicographical Ordering

Define the ring r4 with lexicographical ordering lp:
```
ring r4=complex,(x(7..0),y(7..0)),rp;
```
Define the polynomial *f_1* in the new ring r and print it:
```
poly f_1=x(5)*x(7)+x(5)*x(6)+x(3)*x(7)+x(3)*x(6)+x(2)*x(4)+x(1)*x(7)+x(1)*x(6)+x(1)*x(5)+x(1)*x(3)+x(1)*x(2)+x(0)*x(7)+x(0)*x(3)+x(0)*x(2)+x(6)*y(7)+x(7)*y(6)+x(6)*y(6)+x(7)*y(5)+x(5)*y(5)+x(7)*y(4)+x(1)*y(4)+x(2)*y(3)+x(0)*y(3)+x(6)*y(2)+x(4)*y(2)+x(3)*y(2)+x(0)*y(2)+x(4)*y(0)+x(2)*y(0)+x(7)+x(5)+x(3)+y(7)+y(2)+y(0)+1;
poly f_1;
x(2)*y(0)+x(4)*y(0)+y(0)+x(0)*y(2)+x(3)*y(2)+x(4)*y(2)+x(6)*y(2)+y(2)+x(0)*y(3)+x(2)*y(3)+x(1)*y(4)+x(7)*y(4)+x(5)*y(5)+x(7)*y(5)+x(6)*y(6)+x(7)*y(6)+x(6)*y(7)+y(7)+x(2)*x(0)+x(3)*x(0)+x(7)*x(0)+x(2)*x(1)+x(3)*x(1)+x(5)*x(1)+x(6)*x(1)+x(7)*x(1)+x(4)*x(2)+x(6)*x(3)+x(7)*x(3)+x(3)+x(6)*x(5)+x(7)*x(5)+x(5)+x(7)+1
```
The **reverse lexicographical ordering** is defined from the left to the right: 

1. The monomials are ordered by the lowest variable factor: First we have all monomials with y(0) as a factor, then all monomials with y(1), then all monomials with y(2), etc.
2. Within these groups of `y(0)* ...`, `y(1)* ...`, ..., `x(7)* ...`, ..., `1* ...`, the order of the monomials is determined by the order of the second factor. E. g., `x(2)* y(0)` > `x(4)* y(0)` and `x(2)* x(0)` > `x(3)* x(0)`.
3. The degree of the monomials has no direct impact on the ordering E. g. `y(0)` > `x(0)*y(2)`.



## Macaulay matrix

Y.-A.Chen, X.-S.Gao  describe in their original paper (https://arxiv.org/abs/1712.06239}, 2018) how the matrix is created from a BMQ of a chosen cryptosystem. 


## Online Singular Tool

Check out the online version of the [Computeralgebra System Singular](https://www.singular.uni-kl.de:8003/) to verify our steps:


![](pics/AES_S-Box_ring_vars_singular.png)





