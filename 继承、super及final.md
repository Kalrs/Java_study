### 继承的概念及实现
**父类更抽象更通用，子类更特殊更具体**
- 继承背后的思想是基于已存在的类来构建新类
- 当从已存在类继承时，就重用了他的方法和属性，还可以添加新的方法和属性来定制新类以应对需求
- 约定:从其他导出的类叫子类，被导出的类叫父类
- 在Java中，除了Object类之外，所有的类都是子类，都有唯一的父类  
- 继承在OO中不可或缺
- 创建一个类，总是在继承
- 类之间的关系
  - Is-a 继承体现
  - Has-a 组合体现
  - Like-a 实现接口体现   
- 继承的意义  
  - 代码重用
  - 体现不同抽象曾次
- 父子类关系  
  - 父类更抽象更通用
  - 类更特殊更具体
### extends关键字
- 在Java语言中，用extends关键字来表时一个类继承另一个类
```java
  public  class Teacher extends Person{
   //teacher继承person   
  }
```
### super关键字
#### super关键字特点
- super和this关键字相同:super代表的是父类对象的引用
- 当子父类成员同名,通过super调用
- 子类构造方法中,通过super调用父类构造方法
```java
  public  class Teacher extends Teacher{
  public Teacher (String name,String school){
    super(name,school);//通过调用父类的构造方法完成对相关字段值的初始化
  }
  }
```
**当构造一个子类对象的时候一定会先调用父类的构造方法来构造父类的对象。调用父类的构造方法的语句必须是子类构造方法中的第一条指令**
