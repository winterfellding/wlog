### Dictionary 

##### d.clear()
    
    x = {}
    y = x               # refer to the same dictionary with x
    x['key'] = 'value'
    print y             
    print x     
    x = {}              # x point to the new empty dictionary
    print y             # y still point to the {'key': 'value'} dictionary


    x = {}
    y = x
    x['key'] = 'value'
    print y
    print x
    x.clear()           # when using clear method, x clear the dictionary which it point to, will make y also become an empty dictionary
    print y             # {}

##### d.copy()

    x = {'username': 'admin', 'machines': ['foo', 'bar', 'baz']}
    y = x.copy()
    y['username'] = 'mlh'
    y['machines'].remove('bar')

    # when do replacing value, the original is un affected, when do modify, the original will also change.
    print y         # {'username': 'mlh', 'machines': ['foo', 'baz']}
    print x         # {'username': 'admin', 'machines': ['foo', 'baz']}

    # when we want to copy the totally the value of the original, we can use deepcopy
    from copy import deepcopy
    d = {}
    d['names'] = ['Alfred', 'Bertrand']
    c = d.copy()
    dc = deepcopy(d)
    d['names'].append('Clive')
    print c             # {'names': ['Alfred', 'Bertrand', 'Clive']}
    print dc            # {'names': ['Alfred', 'Bertrand']}

##### get
    
    d = {}
    print d['name']     # will throw KeyError
    print d.get('name') # None, without Error thrown
