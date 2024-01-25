<h1 align = "center">Day01</h1>

### 编译和运行

运行java程序需要先编译"xx.java"文件 ，也叫源代码文件，编译成功后会生成".class"的字节码文件

打开cmd窗口使用 javac命令来编译".java"文件，编译成功后使用java命令来执行生成成功的.class文件

编译可能遇到的错误：

1. 源代码语法错误
2. 编译工具安装失败
3. 源代码文件的编码格式与编译工具的编码格式不一样，例如GBK编译UTF-8就会报错

````java
//	public class test{}	的意思就是定义了一个公有的test类，test{}表示类的开始和结束
//	public static void main(String[] args){}		表示一个主方法，及程序的入口，main(){}	表示方法的开始和结束
//	System.out.println("你好！")；	表示输入  你好  到屏幕上， ; 分号表示结束

public class test{
    public static void main(String[] args){
        System.out.println("你好！")；
    }
}
````

### JDK和JRE

JDK是java开发工具包，JDK的组成部分是由 JRE+java 的开发工具（java，javac，javadoc，javap）组成的，安装了JDK就不用在安装JRE了

JRE是java的运行环境，JRE的组成部分是由JVM + java的核心类库[类]

### Java开发注意事项和细节说明

![image-20240110182820569](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240110182820569.png)

### 转义符

````java
public class ChangeChar{
	public static void main(String[] args){
		//  \t:一个制表位，实现对其的功能		输出结果：北京	上海		天津
		System.out.println("北京\t上海\t天津");
		//  \n:换行符	 		    jack
		//  		      输出结果:smith
		//  					  mary
		System.out.println("jack\nsmith\nmary");
		//  \\:这是一个斜杠\ ，一般使用在输入路径上    输出结果：C:\Windows\System32\cmd.exe
		System.out.println("C:\\Windows\\System32\\cmd.exe");
		//  \":这是一个双引号，和上面类似	   输出结果：老韩说："要好好学java，有钱途"
		System.out.println("老韩说：\"要好好学java，有钱途\"");
		//  \":这是一个单引号，和上面类似	   输出结果：老韩说：'要好好学java，有钱途'
		System.out.println("老韩说：\'要好好学java，有钱途\'");
		//	\r:一个回车，将后面的内容覆盖至前面	输出结果：你门老打电动
		System.out.println("不要老打电动\r你门");	
	}
}
````

### 注释

 // 单行注释  

/*多行注释 */

```java
//这是单行注释
/*
	多行注释
	多行注释
*/	
```

### DOC常用命令

![image-20240110204055542](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240110204055542.png)

![image-20240110204017435](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240110204017435.png)
