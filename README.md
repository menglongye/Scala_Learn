# Scala_Learn
项目描述

##2变量
###2.6数据类型
1. 变量声明时，需要初始化值
2. 在scala中数据类型都是对象
3. scala的数据类型分2大类，anyval(值类型)和AnyRef(引用类型)，不管Anyval还是AnyRef都是对象
4. 在 scala 中有一个根类型 Any ,他是所有类的父类
5. Null 类型是 scala 的特别类型，它只有一个值 null, 他是 bottom calss ,是 所有 AnyRef 类型的子
   类.
6. Nothing类型也是bottomclass,他是所有类的子类，在开发中通常可以将Nothing类型的值返回
   给任意变量或者函数， 这里抛出异常使用很多. 
  

##2.7整数类型
1. Byte Short Int Long
2. Scala各整数类型有固定的表数范围和字段长度，不受具体OS的影响，以保证Scala程序的可 移植性
3. Scala 的整型 常量/字面量 默认为 Int 型，声明 Long 型 常量/字面量 须后加‘l’’或‘L’
4. Scala程序中变量常声明为Int型，除非不足以表示大数，才使用Long

##2.8浮点类型
1. 与整数类型类似，Scala 浮点类型也有固定的表数范围和字段长度，不受具体 OS 的影响。
2. Scala的浮点型常量默认为Double型，声明Float型常量，须后加‘f’或‘F’

##2.9字符类型(Char)
1. 字符常量是用单引号(‘ ’)括起来的单个字符。例如:var c1 = 'a‘ var c2 = '中‘ var c3 =
   '9'
2. Scala 也允许使用转义字符‘\’来将其后的字符转变为特殊字符型常量。例如:var c3 = ‘\n’
   // '\n'表示换行符
3. 可以直接给 Char 赋一个整数，然后输出时，会按照对应的 unicode 字符输出 ['\u0061' 97]
4. Char 类型是可以进行运算的，相当于一个整数，因为它都对应有 Unicode 码.

##2.10布尔类型:Boolean
1. 布尔类型也叫 Boolean 类型，Booolean 类型数据只允许取值 true 和 false
2. boolean 类型占 1 个字节
3. boolean 类型适于逻辑运算，一般用于程序流程控制[后面详解]:

##2.11 Unit类型、Null类型和Nothing类型
1. Null类只有一个实例对象，null，类似于Java中的null引用。
    null可以赋值给任意引用类型 (AnyRef)，但是不能赋值给值类型(AnyVal: 
    比如 Int, Float, Char, Boolean, Long, Double, Byte, Short)
2. Unit类型用来标识过程，也就是没有明确返回值的函数。由此可见，Unit类似于Java里的void。 
    Unit 只有一个实例，()，这个实例也没有实质的意义
3. Nothing，可以作为没有正常返回值的方法的返回类型，非常直观的告诉你这个方法不会正常返 回，
    而且由于 Nothing 是其他任意类型的子类，他还能跟要求返回值的方法兼容。


##2.12.2 值类型隐式转换
1. 有多种类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的那种数据类型，然
   后再进行计算。 5.6 + 10 = 》double
2. 当我们把精度(容量)大 的数据类型赋值给精度(容量)小 的数据类型时，就会报错，反之就会进
     行自动类型转换。
3. (byte, short) 和 char 之间不会相互自动转换。
4. byte，short，char 他们三者可以计算，在计算时首先转换为 int 类型
5. 自动提升原则: 表达式结果的类型自动提升为 操作数中最大的类型

##2.12.4 强制类型转换
1. 当进行数据的 从 大——>小，就需要使用到强制转换
2. 强转符号只针对于最近的操作数有效，往往会使用小括号提升优先级


##2.14 值类型和 String 类型的转换
1. 基本类型转 String 类型 将基本类型的值+"" 即可
2. String 类型转基本数据类型  通过基本类型的 String 的 toXxx 方法即可


##4程序的流程控制
###4.1 程序的流程控制说明
1. 顺序控制 
2. 分支控制
3. 循环控制

##5函数时编程
###5.4.1 基本语法
1. 函数声明关键字为 def (definition)
2. [参数名: 参数类型], ...:表示函数的输入(就是参数列表), 可以没有。 如果有，多个参数使用 逗号间隔
3. 函数中的语句:表示为了实现某一功能代码块
4. 函数可以有返回值,也可以没有
    返回值形式1: 返回值类型=
    返回值形式2:返回值类型不确定 使用类型推导完成
    返回值形式3:没有返回值， return 不生效
5.  如果没有return ，默认执行到最后一行的结果作为返回值


### 5.5.2 函数递归调用的重要的规则和小结
1. 程序执行一个函数时，就创建一个新的受保护的独立空间(新函数栈)
2. 函数的局部变量是独立的，不会相互影响
3. 递归必须向退出递归的条件逼近，否则就是无限递归，死龟了:)
4. 一个函数执行完毕，或者遇到 return，就会返回，遵守谁调用，就将结果返回给谁

###5.6 函数注意事项和细节讨论
1. 函数的形参列表可以是多个, 如果函数没有形参，调用时 可以不带()
2. 形参列表和返回值列表的数据类型可以是值类型和引用类型
3. Scala中的函数可以根据函数体最后一行代码自行推断函数返回值类型。那么在这种情况下， return 关键字可以省略
4. 因为 Scala 可以自行推断，所以在省略 return 关键字的场合，返回值类型也可以省略
5. 如果函数明确使用 return 关键字，那么函数返回就不能使用自行推断了,这时要明确写成
  : 返 回类型 = ，当然如果你什么都不写，即使有 return 返回值为() .
6. 如果函数明确声明无返回值(声明 Unit)，那么函数体中即使使用 return 关键字也不会有返回 值
7. 如果明确函数无返回值或不确定返回值类型，那么返回值类型可以省略(或声明为 Any
8. Scala语法中任何的语法结构都可以嵌套其他语法结构(灵活)，即:函数中可以再声明/定义函数， 
    类中可以再声明类 ，方法中可以再声明/定义方法
9. Scala函数的形参，在声明参数时，直接赋初始值(默认值)，这时调用函数时，如果没有指定实
   参，则会使用默认值。如果指定了实参，则实参会覆盖默认值。
10. 如果函数存在多个参数，每一个参数都可以设定默认值，那么这个时候，
    传递的参数到底是覆 盖默认值，还是赋值给没有默认值的参数，就不确定了(默认按照声明顺序[从左到右])。在这种情况下， 可以采用带名参数
11. 递归函数未执行之前是无法推断出来结果类型，在使用时必须有明确的返回值类型 
12. Scala函数支持可变参数

`注意：`
1. args 是集合, 通过 for 循环 可以访问到各个值。
2. 可变参数需要写在形参列表的最后


  
##6面向对象编程


##8 面向对象编程(高级特性)

###8.1.3 伴生对象
1. 在同一个文件夹中，有class ScalaPerson 和object ScalaPerson
2. class ScalaPerson 成为伴生类，将非静态的北荣写道该类中
3. object ScalaPerson 成为伴生对象，将静态的内容写入到该对象(类)中
4. 对于伴生对象的内容，可以直接通过ScalaPerson. 属性或者方法

### 8.1.6
1. 在伴生对象中定义apply 方法，可以实现 类名(参数) 方式来创建对象是类


//216页
















