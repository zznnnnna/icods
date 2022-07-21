### 使用idea开发Scala

#### 1、安装scala插件
<img src="bigdata/scala/imgs/scala_idea.png" alt="idea" style="zoom:35%;" />

#### 2、安装Scala SDK
<img src="bigdata/scala/imgs/scala_idea2.png" alt="idea2" style="zoom:35%;" />

#### 3、为模块添加Scala的框架支持
<img src="bigdata/scala/imgs/scala_idea3.png" alt="idea3" style="zoom:35%;" />
<img src="bigdata/scala/imgs/scala_idea4.png" alt="idea4" style="zoom:35%;" />
<img src="bigdata/scala/imgs/scala_idea5.png" alt="idea5" style="zoom:35%;" />

#### 4、创建第一个Scala对象
<img src="bigdata/scala/imgs/scala_idea6.png" alt="idea6" style="zoom:35%;" />
<img src="bigdata/scala/imgs/scala_object1.png" alt="object" style="zoom:35%;" />
<img src="bigdata/scala/imgs/scala_object2.png" alt="object2" style="zoom:35%;" />
<img src="bigdata/scala/imgs/scala_object3.png" alt="object3" style="zoom:35%;" />

```scala
object ScalaObjectDemo {

  def main(args: Array[String]): Unit = {
    println("Hello Scala")
  }
}

```
#### 5、Scala重的继承
scala中接口使用trait而不是iterface
scala中不支持类的多继承
scala支持对trait进行多重继承,需要使用with完成多重继承
scala对类和接口的继承都使用extends