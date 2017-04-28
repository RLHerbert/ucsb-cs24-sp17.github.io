# Discussion of The Polynomial Class Using a Fixed Array


Most of the discussion of this assignment is in Section 4.6 of the textbook. Start by making sure that you understand the description of how the coefficients of a polynomial will be stored in an array. The size of the array will be fixed by a constant called CAPACITY. Because of this fixed capacity, the polynomials that you create will have a maximum exponent defined by

```
static const unsigned int MAX_EX = CAPACITY-1;
```

Both CAPACITY and MAX_EX are already defined for you in poly0.h. In your poly0.cxx file, you must declare the memory for these two constants (but not redeclare their values), like this:


```
const unsigned int polynomial::CAPACITY;
const unsigned int polynomial::MAX_EX;
```

A few additional notes about the polynomial operations are given below.
* Constructor

``` 
polynomial(double c = 0.0, unsigned int exponent = 0);
```

This constructor creates a polynomial with one non-zero term. The coefficient and exponent of this term are given by the parameters c and exponent. Notice that the exponent parameter has a default value of zero, so that we can also call the constructor with a single parameter c, for example: polynomial p(42.0);. This creates the polynomial p with the only non-zero term being 42.0 times x to the zero power (which is the same as the number 42.0 since x to the zero power is defined as equal to 1). The parameter c also has a default value of 0.0, so that the constructor can be used with no arguments (in other words, as a default constructor). For example: polynomial p; will create a polynomial p in which all coefficients are zero.

* Modification Member Functions 
```
void add_to_coef(double amount; unsigned int exponent); 
void assign_coef(double new_coefficient; unsigned int exponent); 
void clear( );
```

These are discussed in Section 4.6D on page 214. Do not worry about the reserve function for now.

* Simple Constant Member Functions 

```
double coefficient(unsigned int exponent) const; 
unsigned int degree( ) const; 
double eval(double x) const; 
unsigned int next_term(unsigned int e) const; 
double operator( ) (double x) const;
```

These are discussed in Sections 4.6E and 4.6F on pages 214-215. However, I have slightly changed the return value for NEXT_TERM for the case where there is no next term. In this case, the function should return zero. I have also added a new function (previous_term), specified here:

```
unsigned int previous_term(unsigned int e) const
   POSTCONDITION: The return value is the next exponent n which is SMALLER
   than e such that coefficient(n) != 0.
   If there is no such term, then the return value is UINT_MAX
   from <climits>.
```

Two of these functions, degree and operator(), are defined inline in the header file. Do not try to define them again.

* Derivative 

```
polynomial derivative( ) const;
//For a polynomial p, the value of p.derivative( ) is the first derivative of p.
```

* Arithmetic Operators 

```
polynomial operator +(const polynomial& p1, const polynomial& p2); 
polynomial operator -(const polynomial& p1, const polynomial& p2); 
polynomial operator *(const polynomial& p1, const polynomial& p2);
```

As discussed in Section 4.6G (page 215), these binary operators allow a programmer to write expressions such as p + q.

* Output 

```
ostream& operator << (ostream& out, const polynomial& p);
```

This function writes a polynomial in some easily readable format. See page 79 of the textbook for information on how this output operator is implemented for a class. The information that you print must include the coefficients of all non-zero terms (but no zero terms unless all terms are zero). Some example outputs that would receive full credit:

```
   0
   3.4x^3 + 2.7x^2 + 7.9x + 4
   3.4x^3 - 7.9x
   -3.4x^3 + 5.3
```

Note: Writing this function is possibly the hardest part of the assignment because there are many special cases to consider. Nevertheless, if you give some thought to the organization of these cases beforehand, you can complete the implementation with about 35 lines of code. Be careful if you use an unsigned int to count backward from the degree down to zero (because unsigned ints are not allowed to actually go below zero).


## Requirements for Using Private Member Variables

* CS 24 NOTE
Although not exactly required for PA2, these restrictions are highly recommended, as they really will simplify PA3 and PA4. Later, we will modify our polynomial implementation in several ways. These modifications will be much easier if we put some restrictions on how the private member variables are used. So, for this assignment, you may use the private member variables in the following member functions only:
    
    * The constructor
    * add_to_coef
    * assign_coef
    * clear
    * coefficient
    * degree

* Maintaining the Value of current_degree

Each of the first four functions will make changes to the coef array. After these changes are made, the functions must also adjust the value of current_degree. For example, if a non-zero coefficient is given for an exponent e that is larger than current_degree, then current degree must be adjusted upward to e. There are also several situations where the current_degree must be adjusted downward.

Michael Main, University of Colorado, with small edits by Michael Costanzo.