

## ==2019.5.24==

//为知笔记 谈谈 JavaScript 的作用域

## JavaScript字面量

JavaScript是一种值的记法，“Hello World！”就是一种字符串字面量

==[]是一个空数组==

字面量可以用来定义对象 value={age:12,name:"wangjie",action:function(){}}

## JavaScript 作用域

#### 全局函数作用域

显示声明：var variableName

隐式声明：varibleName = 1

#### 函数作用域

```
function funName(){} //内部

function funName(){return funName()}//闭包

(function(){})() //立即执行函数
```

#### 块级作用域

```
for(var i=0;i<5;i++){} //i在函数内没被释放
```

`let` 和 `const` 关键字，创建块级作用域的条件是必须有一个 `{ }` 包裹

#### 词法作用域

词法作用域是指一个变量的可见性，及其文本表述的模拟值

```
estValue = 'outer';

function afun() {
  var testValue = 'middle';
  
  console.log(testValue);		// "middle"
  
  function innerFun() {
    var testValue = 'inner';
    
    console.log(testValue);		// "inner"
  }
  
  return innerFun();
}

afun();

console.log(testValue);			// "outer"
```

**当我们要使用声明的变量时：JS引擎总会从最近的一个域，向外层域查找；**



## 动态作用域：

在编程中，最容易被低估和滥用的概念就是动态作用域（《JavaScript函数式编程》）。

在 JavaScript 中的仅存的应用动态作用域的地方：`this` 引用，所以这是一个大坑！！！！！

