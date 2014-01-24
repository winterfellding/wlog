###Number
##### / and //
    
    1.0 / 2.0  0.5
    1.0 // 2.0 0.0
    1 / 2      0.5
    1 // 2     0

##### Large Integers

    >>> sys.maxint
    2147483647
    >>> 2147483648
    2147483648L             # max int can be get from sys.maxint

##### input & raw_input

    >>> x = input("x: ")    # input method can be called to get the value from user.
    x: 34
    >>> x
    34
    >>> input("x: ")
    x: 32
    32
    
    >>> input("What's your name?")              #input won't eval the input to string.
    What's your name?Jack

    Traceback (most recent call last):
      File "<pyshell#29>", line 1, in <module>
        input("What's your name?")
      File "<string>", line 1, in <module>
    NameError: name 'Jack' is not defined


    name = raw_input("What is your name? ")
    print "Hello, " + name + "!"
    #newbie answer: input is bad, always use raw_input. 
    #explanation: input will evaluate whatever you put in. So if you write something that can be turned into a number, you will get a number. 

##### normal math method

    >>> pow(2, 3)       # power
    8
    >>> abs(-10)        # absolute
    10
    >>> round(10.3)     # round
    10.0

##### complex number

    >>> import cmath
    >>> cmath.sqrt(-1)
    1j
    >>> cmath.sqrt(1)
    (1+0j)
    >>> (1 + 2j) * (3 + 4j)
    (-5+10j)

##### repr & str
    
    >>> print repr("Hello")    # repr equals ``, it can convert number to string
    'Hello'
    >>> print repr(100L)
    100L
    >>> print str("Hello")
    Hello
    >>> print str(100L)
    100

##### Long String & break line

    wrap string with ''' / """
    >>> 1 + 2 + \
    4 + 5
    12
   

