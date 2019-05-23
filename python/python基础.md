## [1. 数据类型](#数据类型)  
- [1.1. 基本数据类型](#基本数据类型)       
- [1.2. 序列(Sequence)](#序列sequence)        
- [1.3. 字典与集合](#字典与集合)   
- [1.4. 对象高级](#对象高级)     
## [2. 流程控制](#2-流程控制)       
- [2.0.3. 条件判断语句](条件判断语句)        
- [2.0.4. 循环(loop)](#循环loop) 
## [3. 函数](#3-函数)    
- [3.1. 函数的定义](#函数的定义)    
- [3.2. 作用域(scope)](#作用域scope)    
- [3.3. 高阶函数](#高阶函数)  
- [3.4. 闭包(closure)](#闭包closure)    
- [3.5. 装饰器(Decorator)](#装饰器decorator) 
## [4. 面向对象](#4-面向对象)       
- [4.1. 对象(Object)](#对象object)       
- [4.2. 类(Class)](#类class)        
- [4.3. 属性(attribute)](#属性attribute)        
- [4.4. 方法(method)](#方法method)       
- [4.5. 面向对象三大特征](#面向对象三大特征)       
- [4.6. 特殊方法](#特殊方法)   
- [4.7. 设计模式](#设计模式)

# 数据类型
## 基本数据类型
### 数值类型
- int 整型
- float 浮点型
- complex 复数
- 小数失真问题
  python默认是17位小数 , 当要使用更高精度的小数时 , 引入decimal模块 , Decimal数据默认精度为28 , 调用decimal的getcontext() , 设置其中的prec可改变精度

### 布尔类型(bool)
- True和False , 实际为整型的1和0

### 空值(None)

***
## 序列(Sequence)
- 按顺序存储数据的数据结构
- 可以通过index来操作序列中的数据
- 序列的种类
  - 可变序列--列表
  - 不可变序列--元组,字符串
### 序列的通用操作
- in , not in 检查序列中是否包含或不包含某个元素
- \+ 将两个同一类型的序列合并成一个序列
- \* 将某个序列重复多少次
-  len(s) 获取序列的长度
-  min(s) 获取序列中最小的元素
-  max(s) 获取序列中最大的元素
-  s.count(x) 统计元素x在序列s中出现的次数
-  s.index(x,[i [:j] ]) 获取元素x在序列s中第一次出现的位置, i,j 起始结束位置可省略
-  索引操作
   -  s[i] 获取序列索引为i的元素
   -  s[i:j] 切片,获取序列索引从i到j-1的元素
      -  s[:j] 截取从开头到j-1的元素
      -  s[i:] 截取从i到结尾
      -  s[:]  截取所有,相当于浅复制
      -  s[i:j:k] k,截取步长,默认为1,若为负数则从后往前复制
### 序列的解构赋值
- a,b = [1,2] -> a=1 , b=2
使用变量来接受序列中的值,变量数必须和序列中值的个数相等
- a,*b,c = [1,2,3,4] -> a=1 , b=[2,3] , c=4
使用\*可以接受所有没有对应变量的值,并转换成列表

### 列表(list)
- 按顺序存储任意个任意类型数据的数据结构
- 列表是可变序列
- 创建列表
  - lst = [a, b, c]
  - lst = list(a, b, c)  
    *list()方法可以将可迭代对象转换成列表*
- 列表的加乘
  - lst1 = lst1 + lst2 , lst1 = lst1 * 3
  创建新的对象,值为运算后的结构,修改变量lst1的引用
  - lst1 += lst2 , lst1 *= 3
  修改对象的值
  - lst1.extend(lst2)
  修改对象的值
- 可变序列(list)的操作
  - del lst[i] 删除lst中索引为i的元素
  - lst.append(x)  将x添加到lst的末尾
  - lst.insert(i,x) 将x插入到lst中索引为i的位置
  - lst.extend(iterable) 将一个可迭代对象转换成列表,添加到lst的末尾
  - lst.pop(i) 从lst中弹出索引为i的元素,默认末尾元素
  - lst.remove(x)  从lst中删除元素x
  - lst.clear()  清空列表
  - lst.reverse()  反转列表
  - lst.sort(reverse=True)  对列表进行排序,reverse=True降序排序,默认升序
  - 索引操作
    - lst[i] = x  修改lst索引为i的元素为x
    - lst[i:j] = x  对lst的切片进行替换,**切片操作x必须为可迭代对象,然后会进行解构赋值**
      - lst[-1:0] = x  在最后一个元素前添加元素

### 元组(tuple)
- 按顺序存储任意个任意类型数据的数据结构
- 元组是不可变序列
- 创建元组
  -  t = (1,2,3)
  -  t = (1,) *即使只有一个元素也要加逗号*
  -  t = 1,2  *括号可以省略不写*
- tuple()可以将可迭代对象转换成元组
- 元组的加乘
  - s1 = s1 + s2 , s = s * 3
  - s1 += s2 , s *= 3
  都是创建新的对象,赋值,然后修改变量的引用
  
### 字符串(str)
- 使用' '或者" "表示字符串
- 相同的引号不能嵌套 , 单引号不能跨行使用
- ''' '''和""" """来表示长字符串 , 可以跨行使用 , 保留字符串的跨行和缩进
- 本质上是一个不可变序列
- 拼接字符串
  - 使用+将两个字符串连接成一个字符串 , *将指定字符串重复多次
  - 格式化字符串
    ```py 
    a =f'a+{b}' #可以在字符串中直接插入变量
    ```
  - 使用占位符
    - 在字符串中使用占位符,然后占位符进行填充,占位符会替换成指定内容
    - %s 表示任意字符串
    - %d 表示整数
    - %f 表示浮点数, %.nf 表示保留n位小数
    ```py
    a = 'a+%s'%b
    ```
 - 字符串的方法
   - str.isalpha() 检查字符串是否由字母组成
   - 检查是否数字
     - str.isnumeric()  表示数字的 1 ① 一 都返回True
     - str.isdigit()  表示数字的符号 1 ① 返回True
     - str.isdecimal()  必须是阿拉伯数字
   - 检查大小写
     - str.islower()  字符串是否纯小写
     - str.isupper()  字符串是否纯大写
   - 大小写转换
     - str.lower() 将一个字符串转换成小写
     - str.upper() 将一个字符串转换成大写
     - str.title() 将单词的守首母转换成大写
     - str.capitalize() 将字符串的首字母转换成大写
   - 格式对齐
     - str.ljust()  用来对一个字符串进行左对齐
     - str.rjust()  用来对一个字符串进行右对齐
     - str.center() 用来对一个字符串进行居中
     - 参数:
        - width 字符串的宽度
        - fillchar 填充的字符
    - 拆分
      - str.split() 将字符串拆分成一个列表
      - str.rsplit() 从右往左拆分
      - 参数:
        - sep 分隔符,根据其来进行分隔
        - maxsplit 最大的分割数量,默认-1
    - 连接列表
      - str.join(lst) 通过str连接列表 , lst中必须全为字符串
      - eg : '-'.join['1', '2', '3'] -> '1-2-3'  
    - 查找
      - str.find()  查找字符串是否包含某个子串
      - str.rfind()  从右往左查找
      - 参数:
        - sub 查找的字串
        - start 开始查找的位置
        - end 结束查找的位置
      - 返回值
        - 返回子串第一次出现的索引,没有返回-1
      - str.index() , str.rindex() 与之类似,不同在于若未找到则会报错   
    - 去除字符
      - str.rstrip()  去除字符串左边的字符
      - str.lstrip()  去除字符串右边的字符
      - str.strip()   去除字符串两边的字符
      - 参数: 
        - chars 要去除的字符,默认为None,只会去除空白字符' '
    - 检查一个字符串是否以指定内容开头或结尾
        str.startswith() , str.endswith()  
      - 参数:
		chars 指定的字符串
    - 替换
      - str.replace() 字符串中的指定子串
      - 参数
        - old 被替换的字符串
        - new  新的字符串
        - count  要替换的数量,默认为None,全部替换

***
## 字典与集合
### 字典(dict)
- python中对映射(mapping)的实现,由键值对组成,通过key可以快速找到value
- 键(key)
  - key是value的唯一标识
  - 只有不可变对象才可以作为key
  - 一般情况下都是字符串作为key
- 值(value)
  - 字典中储存的数据,可以任意对象
- 创建字典
    ```py
    d = {a:1 , b:2}
    ```
    ```py
    d = dict(a=1 , b=2)
    ```
    ```py
    #dict()方法可以将一个包含双值子序列的序列转换为字典
    a = [('a',1),('b',2)]
    d = dict(a)
    ```
- 字典的使用
  - len(dic) 获取字典的长度
  - key in/not in dic 
    - 检查字典中是否存在某个key
  - dic[key] = value  
    - 通过key来获取或者设置value
    - 获取字典中不存在的key时会报错 , 设置不存在的key-value时会自动添加
  - get(key,[defalut])  
    - 通过key获取value
    - key不存在时返回default,默认为none
  - del dic(key) 根
    - 据key删除字典中的键值对
    - 如果key不存在,则会报错
  - dic.clear() 
    - 清空字典
  - dic.pop(key[,default]) 
    - 根据key弹出(删除并返回)value
    - key不存在时返回default,默认为none
  - dic.popitem()
    - 删除并返回字典中任意的键值对(删除最后一个),返回双值元组
    - 如果对空字典调用会报错
  - dic.setdefault(key[,default])
    - 根据key获取字典的指定值 , 如果key不存在则自动添加
    - key不存在时,设置key-value,value为defalut
  - dic.update(dic2)
    - 将其他字典中的键值对添加到当前字典中
    - 如果字典中没有这个key , 则自动添加 , 如果有则替换
  - dic.copy()
    - 对字典进行浅复制
- 字典的遍历
  - dic.keys() 返回包含字典所有key的可迭代对象
  - dic.values() 返回包含字典所有value的可迭代对象
  - dic.items() 返回包含字典所有key-value双值元组的可迭代对象
### 集合
- 无序的储存不重复数据的数据结构
- 集合中只能储存不可变对象
- 实际上集合就是单独将字典的key提取
- 创建集合
  - s = {1,2,3,4}
  - s = set(1,2,3)
  - 创建空集合只能使用set(), {}创建的是空字典
- 集合的使用
  - len(s)  获取集合的长度
  - in/not in 检查元素是否在集合中
  - s.add(x) 向集合添加元素x,若已存在,则无效
  - s.update(other) 将其他可迭代对象更新到当前集合中
  - s.remove(x) 从集合移除元素x , 若x不存在会报错
  - s.discard(x) 从集合移除元素x , 若x不存在 , 不会报错
  - s.pop() 删除并返回一个集合中的任意元素 , 如果集合为空则报错
  - s.clear()  清空集合
  - s.copy() 对集合进行浅复制
-  集合之间的关系
 - a >= b  检查集合a是不是集合b的父集
 - a <= b  检查集合a是不是集合b的子集
 - a > b  检查集合a是不是集合b的真父集
 - a < b  检查集合a是不是集合b的真子集
- 集合之间的运算
  - & 求两个集合之间的交集
  - |  求两个集合之间的并集
  - \-  求两个集合之间的差集
  - ^  求两个集合之间的异或集 

***
## 对象高级

### 可变对象不可变对象
- 不可变对象
  对象所指向的内存中的值不能被改变
  数值型(int, float, complexe) , str , bool , None , tuple 
- 可变对象
  该对象所指向的内存中的值可以被改变
  list , dict , set

### 深浅复制
- = 赋值操作
  b = a
  - a和b数据完全共享 , 相当a和b指向同一个对象
- 浅复制
  b = a.copy() 
  - a和b数据半共享 , b复制a的数据创建一个新的对象 , 但对象内部引用的对象还是同一个
- 深复制
  b = copy.deepcopy(a)
  - a和b数据完全不共享 , b忘全复制a的数据创建一个新的对象 , 对象内部引用的对象也会创建新的

### 对象池
在编程语言中无论是还是对象池还是线程池 , 都是用来储存一组可以复用的对象 , 把一些常用的对象 , 统一放入到一个对象池中 , 需要时无需创建 , 直接从池中获取 , 避免在反复创建对象的过程中 , 对系统的消耗过大 , 
- 小整数对象池 -- [-5,257)
  这个范围内的整数 , 会长期的保存在python中 , 所以每次引用这些整数 , 指向的都是同一个对象
- 大整数对象池
  大整数对象池中没有常驻对象 , 每次根据执行情况的不同自动添加对象(编译时进行)
  -  执行py文件时 , 解释器会统一对代码进行编译 , 然后交给计算机执行 , 这时大整数就都会引用大整数对象池中的同一个对象
  -  使用交互模式时 , 是边编译边执行 , 大整数对象池中就不会添加对象
- 字符对象池
  字符驻留机制
  - 字符串驻留 , 是指对于简单的字符串 , 不会重复创建 , 而是反复的使用某个对象 
   *简单字符串是指符合标识符规范的字符串*
  - 其原理是引用对象时 ,会先生成一个对象 ,再去和已有的对象比对 , 如果已经有这个对象, 则销毁后使用已有的 , 如果没有 ,使用新建的对象
   *可以减少内存的使用 , 但会降低性能*

# 流程控制
### 条件判断语句
```py
if a>b:
    pass
elif a=b:
    pass
else:
    pass
```
### 循环(loop)
- while循环
```py
while a>b:
    a -= 1
    pass
else:
    pass
```
- for循环
```py
for i in range(100):
    pass
```
- break和countine
  - break 结束循环
  - countine 跳过本次循环
  
***

# 函数

## 函数的定义
- 函数也是对象,也是储存数据容器,只不过函数储存的是可执行的代码块
- 定义函数
  ```py
  def func():
      pass
  ```
- 参数
  - 形参
    - 在定义函数时 , 可以在函数的( )指定数量不等的形参, 使用 , 隔开
    - 定义形参相当于在函数中定义了变量
    - 形参的值在函数调用时才能确认
  - 实参
    - 调用函数时 , 可以向函数中传递实参 , 实参会赋值相应的形参
    - 调用函数可以根据需要传递实参 , 可以传递任意类型的实参
  - 传递参数
    - 位置参数(positional argument)
      - 位置参数根据形参定义的位置顺序传递参数
      - 第一个实参赋值给第一个形参,第二个…
    - 关键字参数(keyword argument)
      - 关键字参数根据形参名来传递参数 , 不考虑参数的顺序 , 只要参数名写对就行
    - 关键字参数和位置参数可以混用,但关键字参数必须写在参数的最后
    - 定义形参可以为参数指定一个默认值
      - 如果传递了实参 , 形参就会是实参的值 , 如果未传递则使用默认值
      - **如果默认值使用的是可变对象 , 每次函数调用时 , 都会共享同一个对象 , 一次修改 , 会影响所有调用**
  - 可变参数
    - 在定义函数时,使用可变参数 , 可以传递任意数量的参数
        ```py
        def func(*args,**kwargs):
            pass
        ```
    - *args只能获取位置参数 , **kwargs可以获取关键字参数
    - *args所有的位置参数保存在一个元组中 , 如果没有参数 , 返回空元组
    - **kwargs会将所有的关键字参数保存到一个字典中 , 字典的key为参数的名字 , 字典的value就是参数的值 
  - 参数拆包
    - 在传递参数时,可以在可迭代对象前加一个*,它会自动将序列中的元素作为位置参数传递
        ```py
        def func(a,b,c):
            pass
        
        a = (1,2,3)
        func(*a)
        ```
    - 字典也可以进行拆包 , 拆包后键值对将作为关键字参数传递
        ```py
        def func(a,b,c):
            pass
        
        dic = {'a':1,'b':2,'c':3}
        func(**dic)
        ```

- 返回值
  - 返回值就是程序执行的结果
  - return 来设置函数的返回值 , return 后可以跟任意的对象
    不写return或return后不跟任何值 , 相当于return None
  - return 一执行函数就立即结束 
- 文档字符串
  - 定义函数时 , 可以在函数开头添加文档字符串 
  - 使用help()调用函数 , 可以查看函数的说明(文档字符串)
    ```py
    def func():
        '''
        这是一个函数
        '''
        pass
    
    help(func)
    ```
  
## 作用域(scope)
  -  作用域就是变量的作用范围
  -  全局作用域
     -  所有写在函数外的内容,都是在全局作用域中
     -  全局作用域在程序执行时创建 , 程序结束时销毁
     -  在全局作用域中定义的变量就是全局变量 , 全局变量可以在任意位置访问
  -  函数作用域
     -  写在函数内的内容都属于函数作用域
     -  函数调用时 , 函数作用域创建 , 调用结束, 作用域销毁
     -  函数每次调用都会创建一个新的作用域 , 每次调用时函数的作用域都是相互独立的
     -  在函数中定义的变量都属于局部变量 , 只能在函数内部访问 , 无法在函数外访问
  -  作用域链
     - 函数作用域在查找变量的过程 
     - 当我们在函数中访问一个变量 , 会优先在当前作用域中寻找 , 如果未找到 , 就去上一级作用域中寻找 , 直至找到全局作用域 , 如果依然没有找到 , 则报错NameError
     - 函数作用域链在其定义时就已经确定了 , 和其调用位置无关
  - 默认情况下 , 在函数作用域中为一个变量赋值 , 这个变量就是局部变量
    在函数中修改全局变量 , 使用global关键子修饰变量
    ```py
    a = 10
    def func():
      global a
      a = 100
    ``` 
  - 在函数作用域中 , 可以修改自身作用域中的变量 , 也可以修改全局作用域中的变量 , 但无法修改上一级作用域中的变量
  
- 命名空间(namspace)
  - 命名空间是存储变量的空间 , 所有的变量都需要储存到命名空间中
    每一个作用域都有其对应的命名空间
  - locals()可以用来获取到当前作用域的命名空间
    globals()可以用来获取全局作用域的命名空间
  - 命名空间实际上就是一个字典对象
    - 当前作用域的所有变量 , 都储存在该字典中 , 变量名就是字典的key , 字典的value就是变量的值
    - 可以通过字典的key来创建变量或者修改变量的值(只适用于全局作用域)
      函数作用域的命名空间是只读的 , 通过locals()对其进行修改没有作用

- 递归函数
  - 自己调用自己的函数就是递归函数 
  - 递归的作用基本和循环一样
  - 递归的核心思想就是将一个大问题拆分成小问题 , 将小问题解决 , 大问题自然解决
  - 递归的要件
    - 终止条件
      - 递归停止的条件
    - 递归条件
      - 如何对问题进行拆分
  ```py
  def func(n):
    '''
      斐波那契数列
    '''
    if n == 1 or n == 2:
      return n
    return func(n-1) + func(n-2)
  ```
- lambda表达式
  - 创建一个匿名函数
  - 语法: lambda 参数:返回值
    ```py
    lambda i:i+1
    ```

## 高阶函数
  参数或返回值是函数的函数
  - filter(function,iterable)
    根据回调函数对可迭代对象中数据进行过滤 , 保留符合条件的数据
    ```py
    filter(lambda i:i%2==0,range(100))
    ``` 
  - sorted(iterable,key=function)
    根据key回调函数对可迭代对象中数据进行排序
    key是可选参数 , 默认情况下为none , 就是对iterable中的数据比较后排序
    ```py
    sorted(range(100),key=lambda i:i*-1)
    ```
  - map(function,iterable)
    map()可以根据回调函数对列表中的数据进行修改 , 然后统一保存到一个新列表中
    ```py
    map(lambda i:i+5,range(100))
    ```
  - reduce()
    reduce根据回调函数的规则对可迭代对象的数据进行累积
    ```py
    from functools import reduce
    reduce(lambda i,j:i+j,range(100))
    ```
## 闭包(closure)
  - 闭包就是能够读取其他函数内部变量的函数 , 主要目的就是隐藏一些不希望被其他函数访问到的数据
  - 函数作用域 , 在函数调用时创建 , 调用结束时销毁. 但是在函数调用结束时 , 如果依然有内部函数对函数中的变量进行引用时 , 此时该函数作用域不会销毁 , 并且该作用域只有其内部函数可以访问 , 形成了闭包.
  - 闭包的要件
    1. 函数的嵌套
    2. 内部函数要引用外部函数的变量
    3. 将内部函数作为返回值返回
   - 形成闭包之后 , 外部函数中的变量只能被内部函数访问 , 变成了一个私有变量
      ```py
      #一个简单的闭包,在outer执行之后,其作用域并没有关闭,可以通过fn()来访问其内部的变量a
      def outer():
        a = 100
        def inner():
          print(a)
        return inner
      fn = outer()
      ```

## 装饰器(Decorator)
  - 装饰器是一种设计模式 , 在不修改函数源码的情况下 , 对函数进行功能上的扩展
  - 其本质上是一个函数 , 可使用 @装饰器名 的语法糖来使用
  ```py
    # @login_required 相当于 fn = login_required(fn) , 将函数传入装饰器
    # 在内部函数inner进行对函数的扩展和调用 , 使用(*args,**kwargs)接受任意数量的目标函数需要使用的位置参数和关键字参数
  def login_required(fn):
    def inner(request,*args,**kwargs):
      if request.is_authenticated:
        return fn(request,*args,**kwargs)
      else:
        return redirect(reverse('user:login'))
    return inner
  ``` 
  - 可以为一个函数指定多个装饰器 , 装饰会按照由内及外的顺序生效
  
***

# 面向对象
- 面向对象编程 , 指的是我们所有的指令都是对某个对象来发
- 面向对象将编程的关注点从过程中剥离 , 转向到对象的设计

## 对象(Object)
- 对象就是对现实世界的抽象 , 对象将事物分为两个部分
  - 数据
    在对象中称为属性(attribute)
  - 功能
    在对象中功能称为方法(method)
- 对象是内存中专门用来存储数据的一块区域 , python中对象是由三个部分组成的(每一个对象中都存储了三个数据)
    1. id(唯一标识)
        - 每个对象都有一个唯一的id , 通过这个唯一的id可以找到对应的对象
        - 使用id()函数来查看对象的id
        - 对于Cpython , 对象的id就是对象的内存地址
        - 任何对象的id都是不能修改的
    2. type(对象的类型)
       - 每个对象都有他的类型 , 类型决定了对象具有哪些功能
       - 使用type()函数来检查对象的类型
       - Python是强类型的语言 , 对象一旦创建 , 类型就无法修改
    3. value(对象中存储的数据)
       - 通过对象的value可不可以改变将对象分为可变对象和不可变对象
- 通过变量引用对象时 , 实际上是在变量中储存了对象的id

## 类(Class)
- python中通过类来创建对象 , 类就是对象的模板 , 决定了对象的结构
- 一个对象是通过某个类来创建的 , 称这个对象是这个类的实例(instance)
- 对象创建流程
  - 当我们调用类来创建对象时 , 在类中会先调用特殊方法__new__() , 使用该方法创建一个新对象 , 并将其创建的对象作为返回值返回
    - __new__的形参为class , 默认传入当前类
    - __new__默认情况下会做以下的事情:
      1. 开辟一块新的内存空间用来储存对象
      2. 将对象的type设置为当前类
      3.  __new__会自动调用实例中的__init__来初始化对象
      4. 将新的对象返回
   -  对象使用完毕 , 会调用__del__来销毁

## 属性(attribute) 
- 属性就是对象的变量
- 公共属性
  - 直接在类中定义的属性 , 是公共属性(类属性) , 保存在类对象中
  - 公共属性可以被所有的实例对象和类对象访问 , 但只能通过类对象修改
  - 一般不将属性添加到类中 , 除非所有实例的属性都一样 , 不同的属性 , 需要通过实例对象来添加
- 实例属性
  - 可以直接向实例对象中添加属性 , 此时属性为实例属性 , 无法被类对象访问
  - 通过特殊方法__init()__对对象进行初始化操作
    - __init()__会在实例对象创建完成之后 , 自动调用
    - 一般将对对象进行初始化的代码全部编写到init()中
    - 当我们调用类创建对象时 , 可以将初始化的参数写在类后的()中 , 类中的参数会自动传递给init() , 再通过init()的self参数添加到当前实例对象中
  ```py
  class Person():
    def __init__(self,name,age):
        self.name = name
        self.age = age

  a = Person('小明',18)
  print(a.name, a.age) #小明 18
  ```
- 访问属性 , 对象.属性名
  - 当读取一个对象的属性时 , 会现在当前实例对象中寻找 , 如果找到了就直接使用 , 未找到的话 , 则去类对象中寻找, 找到了则使用 , 未找到则会去父类的父类寻找直至object , 如果还未找到则会报错
  
## 方法(method)
- 方法就是对象的功能 
- 实例方法
  - 直接在类中定义函数 , 这些函数就会成为对象的方法
  - 调用方法 , 对象.方法()
    - 调用方法时 , 解析器会传递一个默认的参数 , 所以定义方法 , 至少要定义一个形参(self) 
    - 可以通过实例对象调用 , 通过对象调用时 , self不需要手动传递 , 解析器会自动传入 , 传递的是方法的调用者 , 也就是实例对象
    - 也可以通过实例对象调用 , 通过类对象调用时 , 需要手动传入self
- 类方法
  -  在方法前添加@classmethod , 则该方法变成类方法
  -  类方法的第一个参数默认传入cls 表示当前的类
  -  类方法可以通过实例对象和类对象调用
- 静态方法
  - 在方法前添加@staticmethod , 该方法变成静态方法
  - 静态方法可以通过类和实例调用 , 并且没有任何默认参数
  - 静态方法就是和对象无关的方法 , 一般静态方法都是一些工具方法
```py
class Person():
    def __init__(self,name,age):
        self.name = name
        self.age = age
        
    def eat(self):
        print(self.name,'吃饱了~')
    
    @classmethod
    def say_cls(cls):
        print('hahaha',cls)

    @staticmethod
    def drink():
        print('喝酒咯~~')

a = Person('小明',18)
a.eat()  #小明 吃饱了~
a.say_cls() #hahaha <class '__main__.Person'>
a.drink() #喝酒咯~~

Person.eat(a) #小明 吃饱了~
Person.say_cls() #hahaha <class '__main__.Person'>
Person.drink() #喝酒咯~~
```

## 面向对象三大特征
- 封装 , 确保数据的安全性
  - 封装是指将数据储存到对象中 , 通过一些方式控制数据的访问方式 , 用以确保数据的安全性
  - 封装就是就是将属性私有化 , 然后通过gettter和setter方法来提供访问属性和修改属性的权限
  - 好处 , 确保数据的安全性
    1.  可以单独控制属性的可读和可写
    2.  在修改属性时可以对值进行检查 , 确保属性值合法
    3.  对于计算属性 , 可以直接通过方法动态返回
  - 私有属性
    - 在类中 , 可以使用双下划线开头的属性名 , 来隐藏属性
    - 属性或方法一旦添加了双下划线开头 , 其就成为了私有属性 , 只能在类内部被访问 , 不建议在外部访问
    - 实际上以_ _ 开头的的属性 , 在类内部会自动进行改名 , 将属性名修改为 _ _类名_属性名
    - 在开发中 , 一般情况下不需要使用_ _开头 , 私有变量都会以_开头 , 默认约定添加了_的属性是私有属性 , 不要去直接修改 , 而是通过getter或setter来操作
    ```py
    class Person():
      def __init__(self,name,age):
          self.__name = name
          self.__age = age
      def get_name(self):
          return self.__name
      def set__name(self,name):
          self.__name = name

    a = Person('小明',18)
    print(a.get_name()) #小明
    a.set__name('明明')
    print(a.get_name()) #明明
    ```
  - 语法糖
    - 可以使用 @property 装饰器来装饰getter方法 , 简化调用方式
    - 在property装饰过的getter方法后 , 可以通过 @属性名.setter 装饰器来简化
    - 使用这个装饰器简化调用方式时 , 不可单独简化setter
      ```py
      class Person():
      def __init__(self,name,age):
          self.__name = name
          self.__age = age
      @property
      def name(self):
          return self.__name

      @name.setter
      def name(self,name):
          self.__name = name

      a = Person('小明',18)
      print(a.name)    #小明
      a.name = '明明'
      print(a.name)  #明明
      ```
    - 也可通过property()函数来设置getter和setter
      ```py
      class Person():
        def __init__(self,name,age):
            self.__name = name
            self.__age = age
    
        def get_name(self):
            return self.__name

        def set_name(self,name):
            self.__name = name
        name = property(get_name,set_name)

      a = Person('小明',18)
      print(a.name)   #小明
      a.name = '明明'
      print(a.name)  #明明
      ```

- 继承 , 为类提供了可扩展性
  - 子类会自动继承父类的属性和方法 
  - 通过继承 , 可以将子类的共有的属性或方法统一写到父类中 , 然后让子类继承该父类 , 这样我们就不需要在每个类中定义重复的内容
  - 原理
    - 调用对象的一个属性或方法时 , 它会先到当前实例对象中寻找 , 有则使用 , 没有则取类对象中寻找 , 有则使用 , 没有则去父类中寻找 , 以此类推 , 直至到object类中 , 如果依旧没找到 ,则会报错
  - 继承父类后, 可以在子类中创建父类中没有的方法 , 以此对父类进行扩展
    也可子类中创建父类中已有的方法 , 来对父类的方法进行重写
  - 特殊方法也会被继承 , 子类的__init__会重写父类的 
    - 在子类的init中 , 需要定义将父类所需的参数
    - 在init中手动调用父类的init , 直接通过类名调用方法时 , self不会自动传递 , 需要手动传递self
    - 也可以通过super()来调用父类 , 此时不需要手动传递self
    ``` py   
    class Animal():
        def __init__(self,age):
            self.age = age
        
        def eat(self):
            print('吃东西咯')
      

      class Dog(Animal):
        def __init__(self,name,age):
            self.name = name
            #Animal.__init__(self,age)
            super().__init__(age)
        
        def bark(self):
            print(self.name,'汪汪汪~~')

      d = Dog('小白',5)
      print(d.name,d.age) #小白 5
      d.eat()     #吃东西咯
      d.bark()    #小白 汪汪汪~~
    ```
  - 方法
    - isinstance()
      - 可以用来检测某个对象是否是某个类的实例
      - 如果是返回True(父类也会返回True) , 否则返回False
    - issubclass()
      - 用来检测一个类是否是另一个类的子类
    ```py
    print(isinstance(d,Animal))  #True
    print(issubclass(Dog,Animal)) #True
    ```
  - 多重继承
    - 可以为一个类设置多个父类 , 子类就可同时继承多个父类中的方法(属性)
    - 继承顺序:
      第一个父类-->第一个父类的父类-->...-->obeject
      第二个父类-->第二个父类的父类-->...-->obeject
      ...
    - 父类中有相同的属性或方法时 , 前面的父类会覆盖后面的父类

- 多态 , 为对象提供了灵活性
  - 同一操作作用于不同的对象 , 可以有不同的解释 , 产生不同的执行结果
    ```py
    class Cat():    
      def eat(self):
          print('吃鱼咯')
      

    class Dog():
        def eat(self):
            print('吃骨头咯')

    def eat(obj):
        obj.eat()

    c = Cat()
    d = Dog()

    eat(c)  #吃鱼咯
    eat(d)  #吃骨头咯
    ```

## 特殊方法
- 特殊方法都是从object中继承过来的 , 不是由我们自己调用 , 而是在一些特殊情况下 , 由解析器自己调用的方法
- 特殊方法的命名都是以双下划线开头结尾的 , __XXX__
- 当object中未定义我们需要的特殊方法或是其定义的特殊方法我们不满意时 , 我们可重新定义特殊方法
  ```py
  class Cat():    
      def __str__(self):
          return '我是一只猫~~'
      

  c = Cat()
  print(c)
  ```
- 常见特殊方法
  - __new __ , __init __ , __del __
  -  __str __
    当我们调用print()去打印一个对象时 , 他都会先调用str()将对象转换成字符串 , 然后在打印输出 , 而调用str()实际上调用对象的__str__特殊方法 , 该方法返回什么 , 对象就被转换成什么 , 所以我们可以通过修改对象的__str__方法来控制对象的打印输出
  - __repr __
  该方法决定了对象调用repr时的结果 (命令行显示对象信息会调用repr)
  - __bul __
    该方法决定了对象转换成bul值时 , 是True还是False
  - __slots __
    - 在对象中 , 都会将属性储存在一个字典中 , 可以通过__dict__来访问对象的字典
    *字典的查询性能较好 , 但其会消耗大量的内存*
    - 可以通过__slots__属性来指定对象中的属性 , 并将它的值设为由实例属性名的字符串构成的可迭代对象 , 这样在各个实例中会以类似元组的结构储存实例属性 , 可以节省内存 , 但会降低访问性能
  	- 不能向对象中添加 slots 中没有的属性
  	- slots默认不会被子类继承 , 当在子类中设置slots时 , 子类的 slots 会自动包含父类的slots
    ```py
    class Cat():    
      __slots__ = 'name','age'
      def __init__(self,name,age):
          self.name = name
          self.age = age

    c = Cat('旦旦',3)
    print(c.name,c.age) #旦旦 3
    c.gender = 'male' #AttributeError: 'Cat' object has no attribute 'gender'
    ```
  - __call __ 
    - 当一个类具有call方法时 , 类的实例就是一个可调用的对象 , 实例的作用类似于一个函数 , 当将该类的实力调用时 , 就会执行它的call方法
    ```py
    class Cat():    
        def __init__(self,name,age):
            self.name = name
            self.age = age
        def __call__(self):
            print(c.name,c.age)

    c = Cat('旦旦',3)
    c()  #旦旦 3
    ```
    - 主要用来替代闭包 , 使用__call__来定义装饰器
    ```py
    class LoginRequired():
    def __init__(self,fn):
        self.fn = fn
    
    def __call__(self):
        print('装饰器执行了')
        self.fn()
        print('执行结束~~')

    @LoginRequired
    def fn():
        print('我是一个测试函数')

    fn()  #装饰器执行了
          #我是一个测试函数
          #执行结束~~
    ```
  
## 设计模式
- 单例模式
  ```py
  class Only():
      instance = None
      def __new__(cls,*args,**kwargs):
          if not cls.instance:
              cls.instance = object.__new__(cls,*args,**kwargs)
          return cls.instance

  o1 = Only()
  o2 = Only()
  print(o1 is o2)  #True
  ```
- 工厂模式
  工厂模式简单理解，就是将创建的对象的行为从客户端（对象的使用者）处剥离，交由一个函数或方法单独处理，从而对客户端和类进行解耦
  - 工厂方法
    通过一个函数 , 根据传入参数的不同 , 返回不同的对象
    ```py
    class Sneakers():
    pass

    class RunningShoes():
        pass

    class SkateboardShoes():
        pass

    def MakeShoes(brand):
        brand = brand.lower()
        if brand == 'nike':
            return Sneakers()
        elif brand == 'ascis':
            return RunningShoes()
        else barnd == 'vans':
            return SkateboardShoes()
    ```
  - 抽象工厂
    通过一个抽象类 , 将生成对象的方法整合到类中 , 再通过继承和多态 , 继承这个抽象类 , 传入生成不同对象的类
  ```py

  ```
