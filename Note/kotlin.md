# kotlin语言基础

## ==2019.5.24==

## 1. 变量类型自动推断，有点像JavaScript

`val name = "wangjie`

val可以更改地址指向

不是所有变量类型可以自动推断，比如int到long需要手动

## 2.is运算符类型检测

一个不可变的局部变量或者属性，已经判断为某类型，那么检测后不用显式转换，可以直接使用

## 3.字符串与其模板表达式

原始字符串："""三重引号分割 可以包含换行等等任何字符

字符串可以包含模板表达式 \$ 开头

## 4.流程控制语句

### 分支：if when

#### if:

if的分支是代码块，最后的表达式可以是该块的值

kotlin中没有三元表达式

只有一个分支，或者分支结果是Unit，返回值就是Unit

#### when

when比switch更加强大

可以将多个分支合在一起,最后的表达式是分支的值

switch 的default 在when里面是else

`1,2 -> print("1 or 2 ,all this")`

可以用任意表达式（switch 仅仅是常量）作为条件

`parseInt(2)->print("this is integer")`

也可以用in 或者 !in判断一个值在不在其中

`in 10..20->print("x is the range")`

```
val validNumber = arrayOf(1,2,3)
in validNumber -> print("x is the range")`
```

### 循环 for while

#### for

跟平常for循环没什么大的区别

`for(item in collection){}`

如果想通过索引遍历一个数组或者list

`for(i in array.indices){}`

库函数withIndex操作

`for((index,value) in array.withIndex()){}`

### 跳转 break continue return throw

break 和 continue都是控制循环结构 ，break终止整个循环，continue终止本次循环

return 需要显示指定 可以用=来直接返回函数值

return 在 lambda中不一样

普通函数中return是终止函数

匿名或者lambda函数中 return有点像continue

### 标签label

@开头 任意变量 类似goto

可以是类名，方法名，循环名

## 5.修饰符

kotlin/grammar/src/modif iers.grm 中有说明

### classModifier类修饰符

abstract final(不可继承) enum open(可继承类) annotation(注解) sealed(密封类) data(数据类)

### memberModifier方法修饰符

override oepn final abstract lateint(后初始化)

accessModifier 访问权限控制  默认是public

private public protected internal(模块内部可访问)

### varianceAnnotation泛型可变型

in out

## 6.关键字保留字

#### 6.1.this 关键字

this是指向该类的当前对象

this可以和标签结合使用，引用其他作用域的this指针

#### 6.2.super关键字

super指向父类的引用

## 7.操作符和操作符的重载

<https://blog.csdn.net/IO_Field/article/details/52817471>

实现操作符重载的函数应该使用 `operator` 修饰符进行标记.

#### 7.1.操作符优先级

![0b2c36eef45995d6ea481b0452efd86](D:\Desktop\笔记\kotlin.assets\0b2c36eef45995d6ea481b0452efd86.jpg)

#### 7.2.一元操作符

![763ff17186389ecb2f2e4ae7a563870](D:\Desktop\笔记\assets\763ff17186389ecb2f2e4ae7a563870.jpg)

#### 7.3.自增自减运算符

![36aeb3487badeed7fde888def50e9a9](D:\Desktop\笔记\kotlin.assets\36aeb3487badeed7fde888def50e9a9.jpg)

#### 7.4.二元操作符

7.4.1.算术运算符

![4b6674eceeb2e432145c47cf73726dc](D:\Desktop\笔记\kotlin.assets\4b6674eceeb2e432145c47cf73726dc.jpg)

7.4.2.字符串的+运算符重载

## 8.扩展函数扩展属性

扩展函数：接收者类型（被扩展的类型）为前缀

`MutableList<Int>` 添加一个`swap` 函数：

```
fun MutableList<Int>.swap(index1: Int, index2: Int) {
    val tmp = this[index1] // “this”对应该列表
    this[index1] = this[index2]
    this[index2] = tmp
}
```

这个 *this* 关键字在扩展函数内部对应到接收者对象（传过来的在点符号前的对象）

==扩展是静态解析的==

==扩展不能真正的修改他们所扩展的类。==通过定义一个扩展，你并没有在一个类中插入新成员， 仅仅是可以通过该类型的变量用点表达式去调用这个新函数。