# design patterns


# 创建型模式
###工厂模式 factory patter
工厂模式（Factory Pattern）是 Java 中最常用的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。

在工厂模式中，我们在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个共同的接口来指向新创建的对象。
 
 1. 意图：定义一个创建对象的接口，让其子类自己决定实例化哪一个工厂类，工厂模式使其创建过程延迟到子类进行。
 2. 主要解决：主要解决接口选择的问题。
 3. 何时使用：我们明确地计划不同条件下创建不同实例时。
 4. 如何解决：让其子类实现工厂接口，返回的也是一个抽象的产品。
 5. 使用场景：
 6. 优点：
 7. 缺点：
 8. 注意事项：
 
 * 工厂方法模式基于"输入"，应用在超类和多个子类之间的情况，这种模式将创建对象的责任转移到工厂类；
 * 超类可以是接口、抽象类、父类
 
 工厂设计模式的优点
 * 面向接口编程，体现了面向对象的思想；
 * 将创建对象的工作转移到了工厂类；
 
### 抽象工厂模式 abstract factory
抽象工厂模式（Abstract Factory Pattern）是围绕一个超级工厂创建其他工厂。该超级工厂又称为其他工厂的工厂。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。
在抽象工厂模式中，接口是负责创建一个相关对象的工厂，不需要显式指定它们的类。每个生成的工厂都能按照工厂模式提供对象。
 1. 意图： 提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类
 2. 主要解决： 要解决接口选择的问题。
 3. 何时使用：
 4. 如何解决：
 5. 关键代码：
 6. 使用场景：
 7. 优点：
 8. 缺点：
 9. 注意事项：
 
### 单例模式 singleton pattern
单例模式（Singleton Pattern）是 Java 中最简单的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。

这种模式涉及到一个单一的类，该类负责创建自己的对象，同时确保只有单个对象被创建。这个类提供了一种访问其唯一的对象的方式，可以直接访问，不需要实例化该类的对象。


1. 单例类只能有一个实例。
2. 单例类必须自己创建自己的唯一实例。
3. 单例类必须给所有其他对象提供这一实例

#### 懒汉式
    线程安全
    
    非线程安全

#### 饿汉式

#### 双检锁(DCL)double-checked locking

#### 登记式/内部类

#### 枚举式


### 建造者模式 builder pattern
建造者模式（Builder Pattern）使用多个简单的对象一步一步构建成一个复杂的对象。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方式。

一个 Builder 类会一步一步构造最终的对象。该 Builder 类是独立于其他对象的。
 1. 意图：将一个复杂的构建与其表示相分离，使得同样的构建过程可以创建不同的表示。
 2. 主要解决： 主要解决在软件系统中，有时候面临着"一个复杂对象"的创建工作，其通常由各个部分的子对象用一定的算法构成；由于需求的变化，这个复杂对象的各个部分经常面临着剧烈的变化，但是将它们组合在一起的算法却相对稳定。
 3. 何时使用：
 4. 如何解决：
 5. 关键代码：
 6. 使用场景：
 7. 优点：
 8. 缺点：
 9. 注意事项：

# 结构型模式
###适配器设计模式 *adapter*
适配器模式提供了代码重用的方案，即将已有的代码适配或者包装到一些新的接口中，而这些接口在最初设计代码时是没有想到
。
1. 目的  
适配者模式是将现有的旧接口转换为新的客户端接口，我们的目标是尽可能多地用原来已经测试过的代码，并且可以对新接口自由的进行修改。
转换接口使之与不兼容的接口一起工作
