### Scala快速入门
#### 1、Scala安装
>下载
```text
https://www.scala-lang.org/download/all.html
https://www.scala-lang.org/download/2.12.11.html
```
<img src="bigdata/scala/imgs/scala_download.png" alt="download" style="zoom:35%;" />

> 解压

```shell
n@n:~/module$ wget https://downloads.lightbend.com/scala/2.12.11/scala-2.12.11.tgz
n@n:~/module$ tar -xzvf scala-2.12.11.tgz 

```
#### 2、配置环境变量
```shell
n@n:~/module/scala-2.12.11$ pwd
/home/n/module/scala-2.12.11
n@n:~/module/scala-2.12.11$ vim ~/.bash_profile 
export SCALA_HOME=/home/n/module/scala-2.12.11
export PATH=.:$SCALA_HOME/bin:$PATH
n@n:~/module/scala-2.12.11$ source ~/.bash_profile 
```
#### 3、环境验证
```shell
n@n:~/module/scala-2.12.11$ scala
Welcome to Scala 2.12.11 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_333).
Type in expressions for evaluation. Or try :help.

scala> 1+1
res0: Int = 2

scala> res0
res1: Int = 2

scala> res0+2
res2: Int = 4

scala> 
```
#### 4、Scala基础语法

> Scala中的数据类型可以分为两种，基本数据类型和增强版数据类型

基本数据类型： Byte、Char、Short、Int、Long、Float、Double、Boolean
增强版数据类型： StringOps、RichInt、RichDouble、RichChar

> 变量

scala中变量分为可变var和不可变val两种
可变var：可以随时修改生命的变量的值
不可变val：不可以随时修改变量的值
```shell

scala> val a=1
a: Int = 1

scala> var b=1
b: Int = 1
```
声明的变量不论是可变的还是不可变的都可以手动指定变量的类型，如果不手动指定类型Scala会根据值进行自动推断类型
```shell
scala> val c: Int = 3
c: Int = 3

scala> 1 to 10
res0: scala.collection.immutable.Range.Inclusive = Range 1 to 10

scala> 1.toString()
res1: String = 1
```

> 操作符

Scala的操作符与Java几乎没有区别，值得注意的是Scala中没有++、-- 只有+=、-=
```shell
scala> var count=1
count: Int = 1

scala> count++
<console>:13: error: value ++ is not a member of Int
       count++
            ^

scala> count+=1

scala> count
res4: Int = 2
```

> 命令行代码块

如何在命令行执行多行代码？
:paste 代表多行代码的开始
CTRL+D 代表多行代码的结束
使用for循环来测试

> for循环

在for循环可以使用to、until
to是左闭右闭
until是左闭右开
1 to 10 代表1到10
1 until 代表1到9
```shell
scala> :paste
// Entering paste mode (ctrl-D to finish)

val i = 10
for (j <- 1 to i)
print(j)

// Exiting paste mode, now interpreting.

12345678910i: Int = 10

scala> 

scala> :paste
// Entering paste mode (ctrl-D to finish)

val i = 10
for(j <- 1 until 10)
print(j)

// Exiting paste mode, now interpreting.

123456789i: Int = 10

scala> 

scala> for(c<-"hello Scala") println(c)
h
e
l
l
o
 
S
c
a
l
a


```

>集合

集合区别主要是可变集合与不可变集合
可变集合：集合的元素可以动态的修改
不可变集合：元素初始化之后便不可修改
可变集合：在 scala.collection.mutable 这个包下面
不可变集合：在 scala.collection.immutable 这个包下面

> Set

Set集合与Java中的Set集合一样是自动去重的
Set集合也分为可变Set和不可变Set，默认使用不可变Set
Set的常用子类HashSet、LinkedHashSet、SortedSet
HashSet：无序、不重复
LinkedHashSet：有序、不重复、按照插入顺序排序（链表）
SortedSet：有序、不重复、按照元素的自然顺序排序

```shell
scala> val s=Set(1,2,3)
s: scala.collection.immutable.Set[Int] = Set(1, 2, 3)

#这种写法返回一个新的集合
scala> s + 4
res11: scala.collection.immutable.Set[Int] = Set(1, 2, 3, 4)

#这种写法在于改变原集合s 所以会报错
scala> s += 4
<console>:13: error: value += is not a member of scala.collection.immutable.Set[Int]
  Expression does not convert to assignment because receiver is not assignable.
       s += 4
         ^

scala>  val s = scala.collection.mutable.Set(1,2,3)
s: scala.collection.mutable.Set[Int] = Set(1, 2, 3)

#可变Set集合
scala> s += 4
res13: s.type = Set(1, 2, 3, 4)

scala> 
```

> List

List是不可变的
List的两个函数
head：集合的第一个元素
tail：集合第一个元素之后的所有元素

```shell
scala> 

scala> val l=List(1,2,3,4)
l: List[Int] = List(1, 2, 3, 4)

scala> l.tail
res14: List[Int] = List(2, 3, 4)

scala> l.head
res15: Int = 1
```

:: 操作符代表拼接
```shell
scala>  l.head :: l.tail
res16: List[Int] = List(1, 2, 3, 4)

scala> for(i<- l) println(i)
1
2
3
4
```

```shell

```