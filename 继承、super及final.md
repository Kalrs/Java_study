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
### 实例
```java
public class Teacher{
	public static void	main(String [] args){
	/*	B b=new B();
		b.showB();*/
		JavaTeacher java=new JavaTeacher("张三","川师");
		java.teaching();
		DBTeacher DB=new DBTeacher("李四","川师");
		DB.teaching();
	}
	
}
class Tea{
	private String name;
	private String school;
	public Tea(String name,String school){
		this.name=name;
		this.school=school;
	}
	public void teaching(){
		System.out.println("授课准备");
	}
}
class JavaTeacher extends Tea{
	public JavaTeacher(String name,String school){
		super(name,school);
	}
	public void teaching(){
		super.teaching();
		System.out.println("打开eclipse");
		System.out.println("码代码!");
	}
}
class DBTeacher extends Tea{
	public DBTeacher(String name,String school){
		super(name,school);
	}
	public void teaching(){
		super.teaching();
		System.out.println("打开oracl");
		System.out.println("码代码!");
	}
}
/*class A{
	public A(){
		System.out.println("A的构造方法!");
	}
	public void showA(){
		System.out.println("A");
	}
	public void showB(){
		System.out.println("A中的showB()方法");	
	}
}
class B extends A{
	public B(){
		//super();//调用父类的无参数的构造方法,可以省略
		System.out.println("b构造");
}
	public void showB(){
		System.out.println("B");
		super.showB();
	}	
}*/
```
### 方法重写
> 方法重写是指子类可以根据需要对父类继承来的方法进行改写，是多态机制的前奏
- 注意点
  - 重写方法必须和被重写方法具有相同的方法名称、参数列表和返回值
  - 重写方法不能使用比被重写方法更严格的访问权限
  - 父类中私有方法不能被重写 此时写的方法不能叫做重写
  - 在子类重写的方法中继续调用父类父类被重写的方法可以调用super.函数名获取
### final关键字
- final可以用来修饰变量，方法，类。
- final修饰的变量是一个常量。一旦赋了值就不能在被修改。(常量一般都和static关键字配合使用)
- final修饰类代表此类不能被继承。
- final修饰方法表此方法不能被重写。
### 实例
```java
  public	class FinalDemo{
	public static void main(String [] args){
		A a=new A();
		a.showNumber1();
		B b=new B();
		b.showNumber2();
		
		final A a2=new A();
		//a2=new A(); final 用在引用变量上，代表此引用变量
		//只能引用一开始所引用的对象，中途不能改变，不能指向其他对象。
		a2.number2= 5;
		a2.showNumber2();  
	}
}
/*final*/ class A{   //final修饰无法被继承
	public final int number1=1;
	public int number2=2;
	public void showNumber1(){
		//number1++;常量不能被修改;
		System.out.println(number1);
	}
	public /*final*/ void showNumber2(){ //final修饰将无法被重写
		System.out.println(number2);
	}
}
class B extends A{
	public void showNumber2(){
		System.out.println(number2);

}
}

```
### Object类
- Java中，所有类都直接或间接继承子java.lang.Object类，可以说Object是java所有类的祖先及根类
- Java中任何类都继承了Object类中的方法，主要有:
  - String toString() 
     - 返回该对象的字符串描述性信息。默认输出格式是:类名[字段值,字段值...];
     - 只要对象与一个字符串通过“+”连接，系统就会自动调用toString()以获得对象的字符串描述
     - 常被改写: 可以根据用户的需要对其进行重写。
  - boolean equals()
     - Object类原始功能是实现判断两个对象是否具有相同的引用;要求判断两个对象状态的相等性。
     - 在jdk标准库中提供了一些类，比如前面所讲的String,后续所要讲的Date。他们都对equals方法进行了重写。
     - 常被改写: 可以根据用户的需要对其进行重写。
  - hashcode() 
  - clone()
  - getClass()
  - finalize()
### 实例
```jaca
  public	class ObjectDemo{
	
	public static void main(String [] args){
		Student stu1=new Student("小华",55);
		System.out.println(stu1.toString());
		
		Student stu2=new Student("小华",55);
		System.out.println(stu1.equals(stu2));//false
	}
	
	
}
class Student extends Object
{
	private String name;
	private int age;
	public Student(String name ,int age)
	{
		this.name=name;
		this.age=age;
		
	}	
	public String toString(){
		return "姓名:"+name+"年龄:"+age;
	}
	public boolean equals(Object obj){
		//自己跟自己比
		if(this==obj){
			return true;
		}
		if(obj==null){
			return false;
		}
		if(this.getClass()!=obj.getClass()){
			return false;
		}
		Student stu =(Student)obj;
		if(this.age!=stu.age){
			return false;
		}
		if(this.name==null){
			if(stu.name!=null){
				return false;
			}
		}else if(!this.name.equals(stu.name)){
			return false;
		}
		return true;
	}
}

```
