### 常用创建方式
```java
  string s ="超级无敌李大叔啊"；
  string s1="abcd";
  string s2="abcd";
    s1==s2;
   //s1,s2指向同一个字符串池;
```  
### 不常用创建方式
```java
  String s=new string("超级无敌李大叔啊")；
  String s1=new String("abcd");
  String s2=new String("abcd");
  s1!=s2;
  //s1,s2不指向同一个字符串池
```
### String对象特点
- String对象是不可变的  及是常量
- 类中修改String值的方法，其实都是创建了新的String对象
- String的只读特性带来了效率优化可能
- 字符串字面值存储与字符串池中，String对象有限指向该字符串池，避免反复生成重复的字符串实例
- 系统对String的非修改处理效率很高
### String对象的常用方法
- Length()--返回字符串长度
- charAt(int index)--返回指定索引处的char值
- concat(string str)--将指定字符串连接到此字符串尾部
- contains(CharSequence s)--是否包含指定字符串序列
- compareTo(String anotherString)-按字典顺序比较两个字符串
- ·······
### 实例
```java
    public class StringDemo{
	  public static void  main(String [] args){
		String content="hello,超级无敌李大叔!";
		System.out.println(content.charAt(2));
		System.out.println(content.compareTo("hello"));
		System.out.println(content+"这");
		System.out.println(content.endsWith("!"));
		System.out.println(content.startsWith("hello"));
		String s1="abc";
		String s2="abc";
		System.out.println(s1==s2);//true
		String s3=new String("abc");
		String s4=new String("abc");
		System.out.println(s3==s4);//false
		System.out.println(content.indexOf("o"));
		System.out.println(content.lastIndexOf("o"));
	}
}
```
### java对象内存管理机制
 - 使用new常见对象，在堆中分配对象空间，初始化。
 - 在方法栈中定义局部变量，持有对对内存的对象引用
 - 方法执行完返回,栈内存自动释放，局部变量销毁
 - 如果堆内存中对象没有变量引用它，成为垃圾，有垃圾回收器回收，释放堆所占内存
### java垃圾回收器
 - 主要回收堆内存空间
 - 定期扫描，对于被使用的对象加上标记，按可能的路径扫描结束后清楚未加标记的对象
 - 被回收的对像
   - 不再被任何变量引用的对象
   - 引用变量自动放弃
   - 人为将引用变量置为null
