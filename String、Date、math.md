- String对象一旦创建就不能改变。如果需要进行大量的字符串修改操作，应该使用StringBuffer/StringBuilder类或字符数组，最终结果可以被转换成string对象
- StringBuffer 线程安全的可变字符序列
  - 一个类似于String的字符缓冲区，通过某些方法调用可以改变序列的长度和内容
  - 每个字符串缓冲区都有一定容量，未超则无需分配新的内部缓冲区
  - 如果内部缓冲溢出，则增大容量
- StringBuilder
  - JKDK5开始，为StringBuffer补充一个单个线程使用的等价类
  - 优先使用，不执行同步，速度更快
- StringBuilder
  - length()
  - capacity()  容量
  - append(String str) 添加字符
  - insert()  插入
  - indexOf() 查找
  - reverse() 反转
  - tostring() 反转
### 实例
```java
    public class StringBuilderDemo {
	public static void main(String [] args) {
		//StringBuilder d="abc" 没有这种构造方法
		//StringBuilder d=new StringBuilder();//默认16个字符大小
		//StringBuilder ed=new StringBuilder(100);//初始化容量大小的
		//StringBuilder sd=new StringBuilder("abc");
		StringBuilder d=new StringBuilder();
		d.append("Hello world!");
		d.append(1);
		d.append(1.5);
		d.append(true);
		System.out.println(d.length());
		System.out.println(d.capacity());
		d.insert(5, "lee");
		System.out.println(d.toString());
		d.replace(1, 2,"uu");
		System.out.println(d.toString());
		System.out.println(d.indexOf("uu"));
		d.reverse();
		System.out.println(d.toString());
	}
}


```
### 实例
```java
  package my_java;

import java.util.Arrays;

public class MyStringBuilder {
	public static void main(String [] args) {
		Mystr s=new Mystr(100);
		s.append("hello").append("java");
		System.out.println("字符个数:"+s.length());
		System.out.println("总容量"+s.capacity());
		System.out.println(s.toString());
		
		
	}
}
class Mystr{
	private char [] value;//字符数组
	private int count=0;//字符数组中存放字符的个数
	public Mystr() {
		value=new char[16];
	}
	public Mystr(int capaity)
	{
		value = new char [capaity];
	}	
	public Mystr(String str) {
		value=new char[str.length()+16];
	}
	public int length() {
		return count;
	}
	public int capacity() {
		return value.length;
	}
	public Mystr append(String str){
		int len=str.length();//获取长度
		ensureCapacity(count+len);//确保字符数组能放进去所添加的字符串
		str.getChars(0,len,value,count);
		count+=len;
		return	this;
	}
	private void ensureCapacity(int capacity) {
		if(capacity-value.length>0) {
			int newCapacity=value.length*2+2;//扩容后新数组的大小
			Arrays.copyOf(value,newCapacity);
		}
	}
	public String toString() {
		return new String(value,0,count);
	}
	
}
```
### Date
- 构造方法
>pubic Date()
>public Date(long date)
- 常用方法
>public long getTime()
>public void setTime(long time)
>public boolean before(Dare when)
>public int compareTo(Date anotherDate)
>public String toString()









