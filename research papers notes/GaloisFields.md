# Galois Fields for AES

## Topic: Intro to Galois Fields for the AES
*Date:* Dec 10, 2023

YT-Link: https://www.youtube.com/watch?v=x1v2tX4_dkQ

Book: Understanding Cryptography

- Author: Christof Paar

### Summary:
Finite Fields
    - Also called Galois Fields 
	    - To understand field, we need to know what a Ring is.
		    - Ring allows multiple ops like $+,-,\times$ on group.
		    - To understand Ring, we need to know what a Group is.
			    - Group is set of elements with some operation which combines 2 element.
#### Group
- Operation is closed.
	- For any operation, the result belongs to group.

- Operation is associative
	- Sequence is not relevant.

- There is neutral element so any operation with element results in original number e.g. $$1\times x = x$$
- For each element in Group, there is an element $a^{-1}$ called inverse of $a$ such that: $$a \circ a^{-1} = 1$$
	- Not all elements have an inverse.

- Group is **abelian** or **commutative** if $a \circ b = b \circ a$

#### Field or Fields
Also called Galois Fields.
Field is set of numbers in which we can add, multiply, subtract or inverse.
Field is set of elements with following properties:
- All elements form an additive group with group operation $+$ and the neutral element $0$.
- All elements of field except $0$ form a multiplicative group with group operation $\times$ and neutral element $0$.
- When 2 group operations are mixed, the **distributive law** holds, e.g.  $$for \ all \ a,b,c \in F: a(b+c)=(ab)+(ac)$$
- Real and complex numbers are fields.
- In cryptography, we almost always need finite sets.

##### Theorem 4.3.1: 
Finite fields only exists if they have $p^m$ elements where $p$ is prime and $m$ is a positive integer.
###### Example:
- There is a finite field with 11 elements called $GF(11)$ (Galois field 11 or $GF(11^1)$).
- There is a finite field with 81 elements where $GF(81)$ or $GF(3^4)$.
- There is a finite field with 256 elements where $GF(256)$ or $GF(2^8)$ or AES field.
- There is NOT a finite field with 12 elements since $12 = 2^{2}\times 3$ is not in form of $p^m$.
	- A finite field (also known as a Galois field) must have a number of elements equal to a power of a prime number. This requirement stems from the mathematical properties that define a field, particularly the existence of additive and multiplicative inverses for every element.
	- To understand why there can't be a finite field with 12 elements, consider the following points:

		1. **Prime Powers**: A finite field with $( q )$ elements, denoted as $( GF(q) )$, exists if and only if $(q)$ is a power of a prime number. This means $( q = p^n )$, where $(p)$ is a prime number and $(n)$ is a positive integer.

		2. **Field Properties**: In a field, every non-zero element must have a multiplicative inverse. This property imposes restrictions on the number of elements a field can have.

		3. **12 is Not a Prime Power**: The number 12 is not a power of any prime number. It can be factored as $( 12 = 2^2 \times 3)$, which does not fit the form $( p^n )$ with $(n>1)$. The closest prime powers near 12 are $( 2^3 = 8 )$ and $( 3^2 = 9)$, both of which are less than 12, and $(2^4 = 16 )$, which is greater than 12.

	Therefore, since 12 cannot be expressed as a power of a prime number, there cannot be a finite field with exactly 12 elements.

##### Types of FF
- Prime Fields
	- $GF(p^m)$ where $m=1$ is same as $GF(p)$.
- Extension fields
	- $GF(p^m)$ which are specially important in cryptography, written like $GF(2^m)$.
	- AES depends on Extension fields.

##### Prime Fields Arithmetic
The elements of a prime field $GF(p)$ are the integers in set $\{0,1..(p-1)\}$ .
- Add, subtract, multiply
	- let  $a,b\ \in GF(p) = \{0,1..(p-1)\}$ then
		- $a+b\equiv C \mod \  p$ 
		- $a-b\equiv D \mod \  p$  
		- $a\times b\equiv E \mod \  p$ 
	- Note that all conditions of fields are satisfied with these computations
- Inversion
	- $a \in GF(p)$, the inverse $a^{-1}$ must satisfy $a \times a^{-1}\equiv1\ mod\ p$ 
	- this can be computed with Eucl. algorithm.
	- 0 cannot be used for inversion.

##### Extension Fields Arithmetic $GF(2^m)$
- Element representation
	- Elements of $GF(2^m)$ are **polynomials**. So the degree and coefficients are both in $m-1$. Each coefficient is a bit.
		- We look at these as $a_{m-1}\ . \ x^{m-1}+....+a_{1}+a_0$. 
		- $A(x)\in GF(2^m)$
		- if $m=8 \ then$  $a_{8-1}\ . \ x^{8-1}+....+a_{1}+a_0$. 
		- If, $a_{i} \in GF(2) = \{0,1\}$ then it is a prime field.
###### Example: $(GF(2^3))$
$A(x) = a_{2}x^{2}+a_{1}+a_{0}$ = $(a_{1},a_{2},a_{3})$ 
- We can represent $GF(2^3)$ (3-bits --> $(a_{1},a_{2},a_{3})$ ) as 8 elements or $GF(8)$.
- $GF(2^{3)=}\{0,1,x, x+1, x^{2},x^{2}+1, x^{2}+x, x^{2}+x+1\}$ 

| Bits | Bits | Bits |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 0    | 0    | 1    |
| 0    | 1    | 0    |
| 0    | 1    | 1    |
| 1    | 0    | 0    |
| 1    | 0    | 1    |
| 1    | 1    | 0    |
| 1    | 1    | 1    | 




