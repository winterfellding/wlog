### type的比较

python2中可以使用
`import types
type(1) is types.IntType`

python3中使用
`type(1) is int`, 来判定variable的type

也可以使用`isinstance`方法判定。

### Function和Method的比较

function是绑在class上的，如：

    class Account:
      def __init__(self, account):
        self.account = account

    a = Account(100)

`Account.__init__`就是一个function，可以使用`type(Account.__init__)`获得类的名称是function,
`a.__init__`则是一个method,它是一个绑定在object上的方法，使用`type(a.__init__)`获得类的名称是method.
