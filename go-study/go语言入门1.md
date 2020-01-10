### 不知道如何分割的知识点
* go语言的作用域通过{}分割的，每次{}都会有自己的作用域，子域继承或重写父域变量
* go语言不是不需要;分割语句，而是在编译过程中自动插入;来分割语句。阅读分号插入规则 https://golang.org/ref/spec#Semicolons

### Main函数需要注意

1. package名称和文件夹可以不一样，但需要一致，同一个文件夹下的package名称一致
2. 一个项目中通常只有一个main package，main package中通常由一个文件有一个main方法
3. 为测试而建立的项目，可以有多个main package，多个文件中有main方法，只需要执行时编辑执行内容即可

### 变量

* 所有声明而没有复制的变量，均有一个空的数值 int=>0 float=>0.0 string=>"" interface{}=> nil struct=>{} []string=>[] map[string]string=>map[]
* 可以通过nil判断的类型，map，interface，chan，等
* map中值是否存在的判断特殊 data, ok := map[index]; ok {}
* go语言没有自动的类型转换，需要转换时均需要显式的调用方法来实现

### 常量

* 常量需要注意的一点是，如果常量设置了类型则只能赋值给相同类型的变量，如果常量没有设定类型则可以赋值给允许的类型变量。
```cassandraql
   const num int = 10  可以赋值给int类型变量，不可以赋值给int32类型变量
   const num = 10      可以赋值给int，int32，int64类型的变量
```

### 包（package）

* go语言的package类似面向对象编程语言的静态类。
```cassandraql
    package 具有包变量，包变量具有私有和共有差别
    package 通过方法和其他包进行功能和数据交换
    package init方法初始化包变量和包需要的资源内容
```
* init方法
```cassandraql
    包的初始化顺序如下：
    首先初始化包级别（Package Level）的变量
    紧接着调用 init 函数。包可以有多个 init 函数（在一个文件或分布于多个文件中），它们按照编译器解析它们的顺序进行调用。如果一个包导入了另一个包，会先初始化被导入的包。
    尽管一个包可能被导入多次，但只会被初始化一次。
```

### 字符串
* rune类型
* 通过[]byte []rune 进行ascii码同其他uncode字符的转换

### 指针
* 作为函数参数，尽量使用切片(slice)切片本身即是指针，不传递数组或者数组的指针。
* go不支持指针的运算

### 结构体 struct
* 结构体指针
* 以下代码lineA，lineB等效，Go 语言允许我们使用p1.name来代替显式的解引用 (*p1).name
```cassandraql
    type people struct {
        name string
    }
    p1 := &people{name: "zhangsan"}
    fmt.Println(p1.name)    //line A
    fmt.Println((*p1).name) //line B
```
* 嵌套结构体和字段提升，结构体可以相互嵌套，当嵌套结构体为匿名结构体时，嵌套结构体的字段可以提升修改和访问路径
* 结构体比较，如果结构体内的类型可以比较，则结构体可以比较；反之，不可以比较（编译报错）

### 接口 interface
* (interface).(type) 是对interface做的类型断言，不做转换，断言正确后，可以做对应类型的操作
* 接口赋值，如果结构体方法是通过指针类型定义的，接口赋值时，需要赋值结构体（引用类型）

### 标题
* 内容
> 引用 
```
    code
```