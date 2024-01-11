<h1 align = "center">Day02</h1>

### 变量

变量的组成：数据类型+变量名+值

~~~java
//举个例子，声明了一个int类型的a变量，将30赋值给了a
int a = 30；
double b = 99.99;
char c = '男'；
String d = "张三"
~~~

程序中+号的使用：

1. 当左右两边都是数值型时，做加法运算
2. 当左右两边一方为字符串，一方为数值型时，做拼接运算
3. 运算顺序从左往右

~~~java
System.out.println(100 + 20); //120
System.out.println(100 + "20"); //10020
System.out.println(100 + 3 + "hello"); //103hello
System.out.println("hello" + 3 + 100); //hello3100
System.out.println("hello" + 3 + 100); //hello3100
System.out.println("100" + 3 + 50); //100350
~~~

### 数据类型

Java数据类型分为了==基本数据 类型==和==引用数据类型==

##### 基本数据类型

数值型(8种)

```java
//整数类型，存放整数：
byte[1] //占1个字节
short[2] //占2个字节
int[4]
long[8]
//浮点(小数)：
float[4] //占4个字节
double[8]
```

整数类型

整型常量默认为int型，声明long型常量须在后面加上 ‘L’  或  'l'

bit是计算机最小的存储单位，一个 byte 等于 8 bit

~~~java
int n1 = 1L; //错误定义，long类型比int类型更大
long n2 = 1L; //正确定义
~~~

![image-20240111154905959](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111154905959.png)



浮点型

```JAVA
//浮点(小数)：
float[4] //占4个字节
double[8]
```

浮点型有单精度float，双精度double：

关于浮点型在机器中的存放方式是，==浮点数=符号位+指数位+尾数位==

浮点型常量默认是double型，声明float型常量要加上  ‘F’  或  ‘f’ 

~~~java
float num1 = 1.1 //错误定义，在浮点型中默认是double型，这样定义会造成精度丢失
float num1 = 1.1F //正确定义
double num1 = 1.1F //正确定义 
~~~

浮点数使用陷阱

运算比较：

~~~java
//案例演示
public class var04{
        public static void main(String[] args){
        double num1 = 2.7;
        double num2 = 8.1 / 3;
        //num1 和 num2不能直接比较，浮点数运算时结果是一个近似值
        System.out.println(num1); //2.7
        System.out.println(num2); //2.69999997
        if(num1 == num2){
           System.out.println("相等"); 
        }else{
            System.out.println("不相等");  //是不相等的
        }
        }
}
~~~



字符型

char的本质是一个整数，在输出时，是在Unicode码找对应字符：

```java
char[2] //存放单个字符'a'
//案例演示
public class var03{
        public static void main(String[] args){
        char c1 = 'a';
        char c2 = '\t';
        char c3 = '邹';
        char c4 = 97;
        char c5 = 65; 
        System.out.println(c1); // a
        System.out.println((int)c1); // 97,加了转换的int的话，结果就是Unicode内的对应整数，不转换则是a
        System.out.println(c2); // 
        System.out.println(c3); // 邹
        System.out.println((int)c3); // 37049,因为转换了int类型
        System.out.println(c4); // a
        System.out.println(c5); // A
        }
}
```

字符型可以进行运算：

~~~java
System.out.println('A' + 10); // 75 进行了运算，A对应65
char c6 = 'b' + 1;
System.out.println((int)c6); // 99
System.out.println(c6);// c 没有进行转换int，所有结果是99对应Unicode码得到字母c
~~~



布尔型

boolean类型数据只允许取值true和false，没null：

boolean不能用0和非0来表示

```java
boolean[1] //存放true，false
//案例演示
boolean ispass = true;
if( ispass == true){
    System.out.println("恭喜你，答对了");
}else{
    System.out.println("你没有答对，下次努力");
}
   
```

##### 引用数据类型

类

~~~java
class
~~~

接口

~~~java
interface
~~~

数组

~~~java
[]
~~~

![image-20240111102238665](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111102238665.png)



### 基本数据类型转换

![image-20240111163316388](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111163316388.png)

有多种类型的数据混合运算是，系统会首先==自动将所有数据转换成容量最大的那种数据类型==，在进行计算

~~~JAVA
//案例演示
public class var05{
        public static void main(String[] args){
            int n1 = 10;
            //float n2 = n1 + 1.5; //运行的结果类型是double，转成float会丢失精度，所以错误
            float n2 = n1 + 1.5f; //在1.5后加上f声明是float或者用double接收
            double n2 = n1 + 1.5; //用double接收
            System.out.println(n2);
        }
    
}
~~~

当把精度（容量）大的数据类型复制给精度（容量）小的数据类型时，就会报错，要么就会进行自动类型转换

~~~java
int n1 = 1.1 //错误，1.1时double，double -> int大转小，错误
~~~

（byte，short）和char之间不会相互自动转换

~~~java
byte b1 = 10；
char c1 = b1； //错误，byte不能自动转成char
~~~

byte，short，和char它们三者可以计算，在计算时首先转换成int类型

~~~java
byte b2 = 1;
short c2 = 4;
short c3 = c2 + b2; //错误，相加时是int类型，int->short精度丢失
int c4 = c2 + b2; //正确
~~~

boolean不参与转换

~~~java
boolean pass = true；
int a1 = pass；//错误，不参与类型自动转换 
~~~

自动提升原则：表达式结果的类型自动提升为操作数中最大的类型

~~~java
        public static void main(String[] args){
            byte b4 = 1;
            short s3 = 10;
            int num01 = 1;
            float f1 = 10.2F;
            int num02 = b4 + s3 + num01 + f1; //错误，表达式最大的是float类型，float -> int 精度丢失
            float num02 = b4 + s3 + num01 + f1; //正确
            System.out.println(num02);
        }
~~~

##### 强制类型转换

强转可能会造成精度损失或溢出

~~~java
//案例演示
int a1 = (int)1.9;
System.out.println(a1); //结果是1，造成精度损失
int a2 = 2000;
byte b1 = (byte)a2;
System.out.println(a2); //造成数据溢出
~~~

强转符号只针对最近的操作有效，往往会使用小括号提升优先级

~~~java
int x = (int)100 * 3.5 + 6 * 1.5;
//编译错误，(int)100只强转了100，还有double没转，所有这里运算结果是double，double->int
int x = (int)(100 * 3.5 + 6 * 1.5); //正确做法，全部括起来
~~~

基本数据类型-> String

~~~java
int n1 = 100;
float f1 = 1.1f;
boolean b1 = true;
String s1 = n1 + "";
String s2 = f1 + "";
String s3 = b1 + "";
~~~

String-> 基本数据类型

 ~~~java
 String s4 = "123";
 int num1 = Integer.parseInt(s4); //123
 double num2 = Double.parseDouble(s4); //123.0
 boolean b = Boolean.parseBoolean("true"); //true
 ~~~



 