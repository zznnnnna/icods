### Scala面向对象与函数
>1、Scala的函数

在Scala中定义函数需要使用 def 关键字，函数包括函数名、参数、函数体
Scala要求必须给出函数所有参数，返回值不需要给出类型，Scala会推断出返回值类型
函数返回值不需要使用return，默认使用最后一行代码的返回值

```scala
object defs {
 //单行函数
  def sayHello(name: String)=println("hello ,"+name)
//多行函数
  def sayHelloM(name: String,age: Int)={
    println(name+"'s age is "+age)
  }
  

  def main(args: Array[String]): Unit = {
    sayHello("Rex")
    sayHelloM("Rex",24)

  }

}
```

```shell
Rex:24
zzn:22
```

过程函数
函数体没有使用=连接则函数的返回值是Unit，这样的函数称为过程

```scala
//函数写法
  def sayHello1(name: String) = "Hello, " + name
  def sayHello2(name: String): String = "Hello, " + name
//过程写法  
  def sayHello3(name: String) { "Hello, " + name }
  def sayHello4(name: String): Unit = "Hello, " + name
```



> 2、面向对象

类: 使用class关键字、使用new创建对象
```scala
class Person {
  var name = "Scala to Object"

  def sayHell(): Unit = {
    println("hello " + name)
  }

  def getName = name
}

object PersonObject {
  def main(args: Array[String]): Unit = {
    val p = new Person();
    p.sayHell()
   
    println(p.getName)
  }
}
```

```
hello Scala to Object
Scala to Object

```