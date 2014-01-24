### Lists & Tuples

##### Sequence

    >>> seq = [1, 2]
    >>> seq = [[1,2], [2,3]]  # sequence can contains other sequences

    >>> greeting = 'hello'  
    >>> greeting[0]           # index
    'h'
    >>> greeting[-1]
    'o'

    >>> greeting[1: 3]        # slice  
    'el'

    >>> greeting[::2]         # step  
    'hlo'

    >>> [1, 2, 3] + [4, 5, 6] # sequence add
    [1, 2, 3, 4, 5, 6]
    >>> 'Hello, ' + 'world!'
    'Hello, world!'

    >>> [2] * 3               # sequence multiple  
    [2, 2, 2]

    >>> sequence = [None] * 10 # empty list initialize
    >>> sequence    
    [None, None, None, None, None, None, None, None, None, None]

    >>> permissions = 'rw'     # membership
    >>> 'w' in permissions
    True
    >>> 'x' in permissions
    False
    >>> numbers = [1, 2, 3, 4, 5]
    >>> 1 in numbers
    True
    >>> 9 in numbers
    False

    >>> list('hello')               # list function
    ['h', 'e', 'l', 'l', 'o']
    >>> ' '.join('hello')           # join function
    'h e l l o'

    >>> ['to', 'be', 'or', 'not', 'to', 'be'].count('to')       # count function
    2

    >>> a = [1,2,3]                 # extend will change the value of a, and + won't change that
    >>> b = [4,5,6]
    >>> a.extend(b)
    >>> a
    [1, 2, 3, 4, 5, 6]
    >>> b
    [4, 5, 6]