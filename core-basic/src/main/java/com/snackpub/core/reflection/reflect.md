# 类型信息
运行时类型信息使得你可以在程序运行时发现和使用类型信息。  
它使你从只能在编译期执行面向类型的操作的禁锢中解脱了出来,
并且可以使用某些非常,强大的程序。对RTTI的需要,揭示了面向对象设计中许多有趣(并且复杂)的问题,同时也提出了如何组织程序的问题。
## 为什么需要RTTI
RTTI 在运行，时识别一个对象的类型。

## Class 对象
&ensp;&ensp;要理解RTTI在java中的运行原理，首先必须知道类型信息在运行时是如何标识的。
这项工作是由称为Class对象的特殊对象完成的，它包含了与类有关的信息。
事实上，Class对象就是用来创建类的所以后的“常规”对象的。Java使用Class对象来执行其RTTI,即使你正在
执行的是类似转型这样的操作。
<br>
&ensp;&ensp;类是程序的一部分，每个类都有一个Class对象(.class文件)。换言之，每当编写了一个
新类，就会产生一个Class对象。(更恰当地说,是被保存在一个同名的.class文件中)。为了生成这个
类的对象，运行这个程序的Java虚拟机(JVM)将使用被称为“类加载器”的子系统。
<br>
&ensp;&ensp;类加载器子系统实际上可以包含一条类加载器链,但是只有一个**原生类加载器**,它是JVM实现的一部分。原生类加载器加载的是所谓的可信类,包括Java API类,它们通常是从本地盘加载的。在这条链中,通常不需要添加额外的类加载器,但是如果你有特殊需求(例如以某种特殊的方式加载类,以支持Web服务器应用,或者在网络中下载类),那么你有一种方式可以挂接额外的类加载器。
<br>
&ensp;&ensp;所有的类都是在对其第一次使用时,动态加载到JVM中的。当程序创建第一个对类的静态成员的引用时,就会加载这个类。这个证明构造器也是类的静态方法,即使在构造器之前并没有使用static关键字。因此,使用new操作符创建类的新对象也会被当作对类的静态成员的引用。
<br>
&ensp;&ensp;因此, Java程序在它开始运行之前并非被完全加载,其各个部分是在必需时才加载的。这一点与许多传统语言都不同。动态加载使能的行为,在诸如C++这样的静态加载语言中是很难或者根本不可能复制的。
<br>
&ensp;&ensp;类加载器首先检查这个类的Class对象是否已经加载。如果尚未加载,默认的类加载器就会根据类名查找class文件(例如,某个附加类加载器可能会在数据库中查找字节码),在这个类的字节码被加载时,它们会接受验证,以确保其没有被破坏,并且不包含不良Java代码(这是Java中用于安全防范目的的措施之一)。
```java
Class.forName("ClassName")
```
&ensp;&ensp;Class.forName取得Class对象的引用的一种方法。它是用一个包含目标类的文本名的String左输入参数，返回的是一个Class对象
的引用。<u>forName()调用如果这个类型没有加载则加载它。</u>
<br>
&ensp;&ensp;如果Class.forName()找不到你要加载的类，它会抛出异常**ClassNotFoundException**。
<br>
&ensp;&ensp;Class.formName()不需要为了获得Class引用而持有该类型的对象。但是如果你有一个感兴趣的类型了，可以通过调用**getClass()** 方法来获取Class引用，这个方法属于Object的一部分，它将返回该对象的实际类型的Class引用。


## 类型转换前先做检查

