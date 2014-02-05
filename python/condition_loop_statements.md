##### More about print

    >>> print 'Age:', 42    # auto add an space between the characters.
    Age: 42

    print 'Hello,',
    print 'World'

    print 'Hello,', 'World' # these two are doing the same thing. will print out 'Hello, World' (with a space between them)

##### More about import 

    # four ways to use import
    
    import somemodule
    from somemoudle import somefunction
    from somemoudle import somefunction, anotherfunction, yetanotherfunction
    from somemodule import *
    
    #if two moudles have the same named function, e.g. open, we can add the module name before them, such as:
    module1.open(...)
    module2.open(...)

    # we can use from ... import ... as ... to rename the module name in the statements. e.g.
    >>> from math import pi as a
    >>> print a
    3.14159265359

##### More about assignment

    >>> x, y, z = 1, 2, 3
    >>> print x, y, z
    1 2 3

    #  when we want do do value exchange we can just use x, y = y, x , e.g.
    >>> x = 1
    >>> y = 2
    >>> print x, y
    1 2
    >>> x, y = y, x
    >>> print x, y
    2 1

##### the loop/condition are most like the c style language, just use the indent instead of the brackets, and there're some more operators

    >>> 'foo' == 'foo'
    True
    >>> 'foo' is 'foo'
    True
    >>> 1 is not 2
    True

##### reversed

    >>> reversed('hello')
    <reversed object at 0x013493B0>
    >>> list(reversed('hello'))
    ['o', 'l', 'l', 'e', 'h']
    >>> ''.join(reversed('hello'))
    'olleh'

##### Slightly loop

    >>> list(x * x for x in range(10))
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    >>> list(x * x for x in range(10) if x % 3 == 0)
    [0, 9, 36, 81]

##### pass, del

    # pass means do nothing.
    
    # del means delete the refrence, means the name is not defined anymore, and will not affect other names. e.g.
    >>> x = ['Happy', 'New', 'Year']
    >>> y = x
    >>> y[2] = 'Python'
    >>> x
    ['Happy', 'New', 'Python']
    >>> del x
    >>> y
    ['Happy', 'New', 'Python']