# DesignPattern
##Java 设计模式（观察者模式、工厂模式、策略模式等）

###参照Hongyang的CSDN博客所写：
>[http://blog.csdn.net/lmj623565791/article/category/2206597](http://blog.csdn.net/lmj623565791/article/category/2206597)

###一. Blog Catalogue：
####1. [设计模式 观察者模式 以微信公众服务为例](http://blog.csdn.net/lmj623565791/article/details/24179699)

####2. [设计模式 工厂模式 从卖肉夹馍说起](http://blog.csdn.net/lmj623565791/article/details/24460585)

-----
###二. 简单解释
####1. 观察者模式
 - 定义了对象之间的一对多的依赖，这样一来，当一个对象改变时，它的所有的依赖者都会收到通知并自动更新。

 - 对于JDK或者Andorid中都有很多地方实现了观察者模式，比如XXXView.addXXXListenter ， 当然了 XXXView.setOnXXXListener不一定是观察者模式，因为观察者模式是一种一对多的关系，对于setXXXListener是1对1的关系，应该叫回调。

 - 专题接口：[Subject.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/observer/interfaces/Subject.java) ;  3D服务号的实现类：[ObjectFor3D.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/observer/classs/ObjectFor3D.java)
 - 所有观察者需要实现此接口:[Observer.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/observer/interfaces/Observer.java)

####2. 工厂模式
简单列一下这个模式的家族：

- 1、静态工厂模式

	- 这个最常见了，项目中的辅助类，TextUtil.isEmpty等，类+静态方法。

- 2、简单工厂模式（店里买肉夹馍）

	- 根据类型直接创建肉夹馍：[SimpleRoujiaMoFactory.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/classs/SimpleRoujiaMoFactory.java)

- 3、工厂方法模式(开分店)
	-  定义：定义一个创建对象的接口，但由子类决定要实例化的类是哪一个。工厂方法模式把类实例化的过程推迟到子类。
	-  对比定义：
  	 - 1、定义了创建对象的一个接口：public abstract RouJiaMo sellRoujiaMo(String type);
 	 - 2、由子类决定实例化的类，可以看到我们的馍是子类生成的。
 - 提供创建肉夹馍抽象方法：[RoujiaMoStore.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/gcff/RoujiaMoStore.java)
 - 实现抽象方法：[XianRoujiaMoStore.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/gcff/XianRoujiaMoStore.java)
 - 分店依旧使用简单工厂模式：[XianSimpleRoujiaMoFactory.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/gcff/XianSimpleRoujiaMoFactory.java)

- 4、抽象工厂模式
	 - 定义：提供一个接口，用于创建相关的或依赖对象的家族，而不需要明确指定具体类。
	 - 对比定义：
	 	- 1、提供一个接口：public interface RouJiaMoYLFactroy
	 	- 2、用于创建相关的或依赖对象的家族 public Meat createMeat();public YuanLiao createYuanliao();我们接口用于创建一系列的原材料。
	 - 创建用于提供原料的接口工厂：[RoujiaMoYLFactory.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/cxgc/RoujiaMoYLFactory.java)
	 - 各自分店实现接口，完成原料提供：[XianRoujiaMoYLFoctory.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/cxgc/XianRoujiaMoYLFoctory.java)
	 - 准备时，使用官方的原料：[RoujiaMo.java](https://github.com/youlookwhat/DesignPattern/blob/master/app/src/main/java/com/example/jingbin/designpattern/factory/cxgc/RoujiaMo.java)
 
---

###三. Thanks
- [CSDN:张鸿洋](http://blog.csdn.net/lmj623565791)