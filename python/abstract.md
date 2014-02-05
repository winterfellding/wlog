### Abstraction

##### abstract method

    # the fibonacci number functions
    def fibonacci(num):
        if num <= 1:
            print "Your number is too small."
        else:
            fibs = [0, 1]
            for i in range(num - 2):
                fibs.append(fibs[-2] + fibs[-1])
            print fibs

    if __name__ == '__main__':
        num = raw_input('Please input your number: ')
        fibonacci(int(num))

    # __doc__ return the documents of the function
    >>> from math import sqrt
    >>> print sqrt.__doc__
    sqrt(x)

    Return the square root of x.