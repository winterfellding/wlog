### String

##### C kind pre-format

    >>> print "Hello %s" % ("World")
    Hello World
    >>> from math import pi
    >>> format = "PI with three decimals: %.3f"
    >>> print format % pi
    PI with three decimals: 3.142

##### Template Strings
    
    >>> from string import Template
    >>> s = Template('$x, where did you go these days?')
    >>> s.substitute(x = 'Jack')
    'Jack, where did you go these days?' # if want to insert dollar sign, use $$

##### String methods

    >>> "Hello".find('lo')      # find
    3
    >>> "Hello".find('a')       # failed to find, return -1
    -1
    >>> "Hello".find('l')       
    2
    >>> "Hello".find('l', 2)    # with the string want to find and the index start with.
    2
    >>> "Hello".find('l', 3)
    3
    >>> seq = ['1', '2', '3']   # join
    >>> '+'.join(seq)
    '1+2+3'
    >>> "HELLO".lower()         # lower
    'hello'
    >>> "Hello, Jack".replace("Jack", "Tom")    # replace
    'Hello, Tom'
    >>> "1,2,3,4,5".split(',')  # split
    ['1', '2', '3', '4', '5']
    