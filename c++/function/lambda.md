无名函数的返回值是decltype(x+y)。如果lambda函数体的形式是return expression，或者什么也没返回，或者所有返回语句用decltype都能检测到同一类型，那么返回值类型可以被省略:
***
