Algorithm for Newton's Method of finding a polynomial root

assert precondition that epsilon must be greater than zero
calculate derivative of the polynomial
set answer to starting guess
initialize a variable f by evaluating polynomial at answer
initialize a variable fprime by evaluating derivative at answer
set iterations to 0
loop until maximum iterations or until either |f| or
    |fprime| is less than or equal to epsilon:
        increment iterations
        calculate new answer as prior answer - f / fprime
        reset f by evaluating polynomial at new answer
        reset fprime by evaluating derivative at new answer
set success true if |f| is less than epsilon, or false otherwis