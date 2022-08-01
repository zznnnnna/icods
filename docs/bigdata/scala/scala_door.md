### Scala快速入门
#### 1、Scala安装
>下载
```text
https://www.scala-lang.org/download/all.html
https://www.scala-lang.org/download/2.12.11.html
```
<img src="bigdata/scala/imgs/scala_download.png" alt="download" style="zoom:35%;" />

> 解压

```shell script
n@n:~/module$ wget https://downloads.lightbend.com/scala/2.12.11/scala-2.12.11.tgz
n@n:~/module$ tar -xzvf scala-2.12.11.tgz 

```
#### 2、配置环境变量
```shell script
n@n:~/module/scala-2.12.11$ pwd
/home/n/module/scala-2.12.11
n@n:~/module/scala-2.12.11$ vim ~/.bash_profile 
export SCALA_HOME=/home/n/module/scala-2.12.11
export PATH=.:$SCALA_HOME/bin:$PATH
n@n:~/module/scala-2.12.11$ source ~/.bash_profile 
```
#### 3、环境验证
```shell script
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
```shell script

scala> val a=1
a: Int = 1

scala> var b=1
b: Int = 1
```
声明的变量不论是可变的还是不可变的都可以手动指定变量的类型，如果不手动指定类型Scala会根据值进行自动推断类型
```shell script
scala> val c: Int = 3
c: Int = 3

scala> 1 to 10
res0: scala.collection.immutable.Range.Inclusive = Range 1 to 10

scala> 1.toString()
res1: String = 1
```

> 操作符

Scala的操作符与Java几乎没有区别，值得注意的是Scala中没有++、-- 只有+=、-=
```shell script
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

>while循环

```shell script

scala> :paste
// Entering paste mode (ctrl-D to finish)

var n = 0
while(n<10){
println(n)
n += 1
}

// Exiting paste mode, now interpreting.

0
1
2
3
4
5
6
7
8
9
n: Int = 10

```


> for循环

在for循环可以使用to、until
to是左闭右闭
until是左闭右开
1 to 10 代表1到10
1 until 代表1到9
```shell script
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


#高级for循环
scala> for(i<- 1 to 10 if i%2==0) print(i)
246810

```

>集合

集合区别主要是可变集合与不可变集合
可变集合：集合的元素可以动态的修改
不可变集合：元素初始化之后便不可修改
可变集合：在 scala.collection.mutable 这个包下面
不可变集合：在 scala.collection.immutable 这个包下面

>Set

Set集合与Java中的Set集合一样是自动去重的
Set集合也分为可变Set和不可变Set，默认使用不可变Set
Set的常用子类HashSet、LinkedHashSet、SortedSet
HashSet：无序、不重复
LinkedHashSet：有序、不重复、按照插入顺序排序（链表）
SortedSet：有序、不重复、按照元素的自然顺序排序

```shell script
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

```shell script
scala> 

scala> val l=List(1,2,3,4)
l: List[Int] = List(1, 2, 3, 4)

scala> l.tail
res14: List[Int] = List(2, 3, 4)

scala> l.head
res15: Int = 1
```

:: 操作符代表拼接
```shell script
scala>  l.head :: l.tail
res16: List[Int] = List(1, 2, 3, 4)

scala> for(i<- l) println(i)
1
2
3
4
```

>Map

**不可变Map**
```shell script

scala> val names= Map("name1"->"Rex","name2"->"Simon","name3"->"Gordon")
names: scala.collection.immutable.Map[String,String] = Map(name1 -> Rex, name2 -> Simon, name3 -

scala> names("name1")
res1: String = Rex
```
**可变Map**
```shell script
scala> val mulnames=scala.collection.mutable.Map("name1"->"Rex","name2"->"Simon","name3"->"Gordon")
mulnames: scala.collection.mutable.Map[String,String] = Map(name2 -> Simon, name1 -> Rex, name3 -> Gordon)

scala> mulnames("name2")
res0: String = Simon

scala>

```
**Map另一种定义方式**
```shell script

scala> val ages=Map(("age1",22),("age2",23))
ages: scala.collection.immutable.Map[String,Int] = Map(age1 -> 22, age2 -> 23)

scala> ages("age1")
res0: Int = 22

scala>

```

**MAP的函数**

contains: 检查Map中的key是否存在
getOrElse：如果key存在则返回value，否则返回参数2
```shell script

scala> val age3=if(ages.contains("age3")) ages("age3") else 0
age3: Int = 0

scala> val age=ages.getOrElse("age3",0)
age: Int = 0
```

**编辑修改Map**

```shell script

scala>  val mulnames=scala.collection.mutable.Map("name1"->"Rex","name2"->"Simon","name3"->"Gord                   on")
mulnames: scala.collection.mutable.Map[String,String] = Map(name2 -> Simon, name1 -> Rex, name3 -> Gordon)

scala>
#新增元素
scala> mulnames("name4")="zzn"

scala> mulnames
res1: scala.collection.mutable.Map[String,String] = Map(name2 -> Simon, name1 -> Rex, name4 -> zzn, name3 -> Gordon)
#新增多个元素
scala> mulnames+=("name5"->"ls","name6"->"wbj")
res3: mulnames.type = Map(name2 -> Simon, name5 -> ls, name1 -> Rex, name4 -> zzn, name3 -> Gordon, name6 -> wbj)
#移除元素
scala> mulnames-="name6"
res4: mulnames.type = Map(name2 -> Simon, name5 -> ls, name1 -> Rex, name4 -> zzn, name3 -> Gordon)
#遍历entrySet
scala> for((key,value)<-mulnames) println(key+" "+value)
name2 Simon
name5 ls
name1 Rex
name4 zzn
name3 Gordon
#遍历key
scala> for(key<-mulnames.keySet) println(key)
name2
name5
name1
name4
name3
#遍历value
scala> for(value<-mulnames.values) println(value)
Simon
ls
Rex
zzn
Gordon
```

**Map的子类**

HashMap：针对key的hash值进行存储、可变可不变
SortedMap：自动对Map的key进行排序【自然顺序】、不可变
LinkedHashMap：以key-value的插入顺序保持顺序、可变

>Array

与Java中的Array类似，是长度不可变的，底层其实就是Java数组
```shell script

scala> val arr=new Array[Int](10)
arr: Array[Int] = Array(0, 0, 0, 0, 0, 0, 0, 0, 0, 0)

scala> arr(0)
res0: Int = 0

scala> arr(0)=1

scala> arr(0)
res2: Int = 1

scala> val ar=Array("Rex","Simon","Gordon")
ar: Array[String] = Array(Rex, Simon, Gordon)

scala> ar(2)
res3: String = Gordon

```

>ArrayBuffer

**可变的数组**

```shell script
scala>  import scala.collection.mutable.ArrayBuffer
import scala.collection.mutable.ArrayBuffer

scala> val b=new ArrayBuffer[Int]()
b: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer()
#新增元素
scala> b+=1
res5: b.type = ArrayBuffer(1)
#新增多个元素
scala> b+=(2,3,4)
res6: b.type = ArrayBuffer(1, 2, 3, 4)
#在3角标新增元素
scala> b.insert(3,5)

scala> b
res8: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer(1, 2, 3, 5, 4)
#移除角标3的元素
scala> b.remove(3)
res9: Int = 5

scala> b
res10: scala.collection.mutable.ArrayBuffer[Int] = ArrayBuffer(1, 2, 3, 4)

#函数
scala> val c=Array(3,4,1,2,8)
c: Array[Int] = Array(3, 4, 1, 2, 8)
#元素和
scala> val sum=c.sum
sum: Int = 18
#元素最大值
scala> val max=c.max
max: Int = 8
#快速排序
scala> scala.util.Sorting.quickSort(c)

scala> c
res12: Array[Int] = Array(1, 2, 3, 4, 8)


```

>Tuple

Tuple：元组，与Arry一样都是不可变的。Tuple的角标从1开始，Array角标从0开始。
Scala中的元组最大长度为22，针对更大长度推荐集合、数组

```shell script

scala> val tup=(1,"Rex",24)
tup: (Int, String, Int) = (1,Rex,24)

scala> tup._1
res13: Int = 1

scala> tup._2
res14: String = Rex

```
##### 总结
**可变集合： LinkedHashSet、ListBuffer、ArrayBuffer、LinkedHashMap**
**可变+不可变集合： Set、HashSet、SortedSet、Map、HashMap**
**Array：长度不可变、里面的元素可变**
**Tuple：长度不可变、元素不可变**