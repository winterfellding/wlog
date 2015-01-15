##### BootStrap form中的button点了自动提交form

      今天在写个功能的时候碰到个问题，在使用Bootstrap框架写页面的时候，form元素中有个button
    元素，上面绑定着一个js方法，但点了之后后台不跑js方法，直接跑了form提交的代码。
      查了一下后，Bootstrap中form元素中的button元素，如果不给上type的话，会自动判定
    为type＝"submit"，所以自动判定成了form提交，导致了不跑绑定的js方法。