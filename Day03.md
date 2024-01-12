<h1 align = "center">Day03</h1>

### 运算符

运算符是一种特殊符号，用以表示数据的运算、赋值和比较等。

1. 算数运算符

   ![image-20240112103147098](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112103147098.png)

   /	除	

   ~~~java
   //案例演示
   System.out.println(10 / 4); //数学中等于2.5，在java中两个整数相除会直接取整数，所有等于2
   System.out.println(10.0 / 4);//声明了10.0为double类型,结果是2.5
   double d1 = 10 / 4; //在java中结果等于2，把2赋值给double，等于2.0
   System.out.println(d1);
   ~~~

   % 取模（取余数）

   公式  a % b = a - a / b * b

   ~~~java
   System.out.println(10 % 3); //1
   // -10 - (-10) / 3 * 3 = -1
   System.out.println(-10 % 3); //-1
   // 10 - 10 / (-3) * (-3) = 1
   System.out.println(10 % -3); //1
   // (-10) - (-10) / (-3) * (-3) = -1
   System.out.println(-10 % -3); //-1
   ~~~

   ++ 自增

   a++ 等价于 a = a + 1

   ~~~java
   int i = 8;  //最后结果是10
   //后++，表示先赋值后自增，等价于k=i，然后i自增，i+1，现在i是9
   int j = i++; //8
   //前++，表示先自增后赋值，等价于i=i+1，k=i，i=9+1，i10，k=10；
   int k = ++i; //10
   System.out.println("i=" +i +"\n"+ "j=" + j +"\n"+ "k=" + k); 
   ~~~

   练习题

   ~~~java
   // 假如还有59天放假，那么还有多少个星期零多少天
   class arithmetic04{
   	public static void main(String[] args){
   		int xq = 59 / 7;
   		int day = 59 % 7;
   		System.out.println("还有" + xq +"个星期零"+ day + "天就放假了"); 
   }
   } 
   
   //定义一个变量保存华氏温度，华氏温度转换摄氏温度的公式为： 5/9*(华氏温度-100)
   //请求出华氏温度对应的摄氏温度。
   class arithmetic05{
   	public static void main(String[] args){
   		double hswd = 130;
   		double sswd = 5.0 / 9.0 * (hswd - 100);
   		System.out.println("今天的华氏温度是" + hswd +"\n" + "今天的摄氏温度是" + sswd); 
   }
   } 
   ~~~

   

2. 关系运算符[比较运算符]

   ![image-20240112135126056](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112135126056.png)

3. 逻辑运算符

   ![image-20240112135710444](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112135710444.png)

   |    1     |    2    |
   | :------: | :-----: |
   | 短路与&& | 逻辑与& |

   短路与和逻辑与，只有两个都为true，那就是true，只要有一个是false，那全是false

   短路与&& 和 逻辑与& 区别

   短路与执行时只要执行到false，那就不会继续执行（效率高）

   逻辑与执行到了false，会继续执行，但是结果不会变，还是false

   ~~~java
   int a = 12;
   int b = 90;
   if (a > 20 & ++b < 100){ //逻辑与，a>20是flase，但是还会继续执行 ++b
      //(a > 20 & ++b < 100)//短路与，a>20是flase，不会继续执行后面的判断
       System.out.println("嘿嘿00"); //false
   }
   System.out.println("a=" +a + "\n" + "b=" +b);//a=12,b=91
   
   ~~~

   

   |     1      |    2     |
   | :--------: | :------: |
   | 短路或\|\| | 逻辑或\| |

   只要有一个为true，那么就都为true，否则false

   短路或|| 和 逻辑或| 区别

   短路或只要执行到了true，就不会往下继续执行（效率高）

   逻辑或则执行到了true或false，都会把剩余的执行完成

   ~~~java
   int a1 = 12;
   int b1 = 90;
   if (a1 > 20 | ++b1 < 100){
       System.out.println("嘿嘿00"); 
   }
   if (a1 < 20 | ++b1 < 10) {
       System.out.println("嘿嘿11");
   ~~~

   

   |   1    |     2     |
   | :----: | :-------: |
   | 取反！ | 逻辑异或^ |

   取反！，结果为true，那就是false，结果为false，那就是true

   ~~~java
   System.out.println(!(60>20));//取反，结果为false
   ~~~

   逻辑异或^，两个结果不同时，结果为true，否则为false

   ~~~java
   boolean b = (10 > 5) ^ (9 > 2); //两个结果相同
   System.out.println("b=" +b); //false,结果不同则为true
   ~~~

4. 赋值运算符

   |  1   |                 2                 |
   | :--: | :-------------------------------: |
   |  =   | 复合赋值运算符+=、-=、/=、*=..... |

   ![image-20240112152305458](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112152305458.png)

   赋值运算符的运算顺序是从右往左

   赋值运算符的左边只能是变量，右边可以是变量，表达式，常量值

   复合赋值运算符比如a+=3，等价于a = a + 3；

   复合赋值运算符会进行类型转换

   ~~~java
   int a = 10;
   a += 4;//14  a = a + 4
   ~~~

   

5. 三元运算符

   基本语法：条件表达式？表达式1：表达式2；

   运算规则：

   条件表达式true，结果就是表达式1；

   条件表达式false，结果就是表达式2；

   ~~~java
   int a = 10;
   int b = 123;
   //a > b为false，所有执行表达式2,result = 123,b自减，b = 122
   int result = a > b ? a++ : b--;
   ~~~

运算符优先级

![image-20240112160435667](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112160435667.png)

### 标识符的规则和规范

变量、方法和类等命名时使用的字符序列称叫标识符

凡是自己可以起名字的地方都叫标识符

规则：

1. 由英文，数字，下划线_和$组成
2. 数字不能开头
3. 不能使用关键字和保留字
4. 严格区分大小写，长度无限制
5. 不能包含空格

规范：

1. 包名，全小写，多个英文单词使用点  .  aa.bb.cc
2. 类名，接口名，首字母大写，所有单词首字母大写 TankShotGame(大驼峰)
3. 变量名、方法名,首字母小写，其他字母首字母大写，helloWord（小驼峰）
4. 常量名，所有大写，多个单词则用下划线_区分，TAX_RATE

 ### 键盘输入语句

~~~java
//把java.ntil下面的Scanner类导入
import java.util.Scanner;
public class arithmetic10{
	public static void main(String[] args){
		//Scanner类表示简单文本扫描器，在java.ntil包
		//创建一个Scanner对象，new就是创建，myScanner对象
		Scanner myScanner = new Scanner(System.in);
		System.out.println("请输入你的姓名：");
		String name = myScanner.next();//接收用户输入String
		System.out.println("请输入你的年龄：");
		short age = myScanner.nextShort();//接收用户输入short
		System.out.println("请输入你的薪水：");
		double money = myScanner.nextDouble();//接收用户输入double
		System.out.println("姓名是" + name + "年龄是" + age + "薪水是" + money);
		}
} 
~~~



### 进制

1. 二进制：0，1，以0b或0B开头，满2进1

   ~~~java
   int n1 = 0b1010;
   ~~~

2. 十进制：0-9，满10进1

   ~~~java
   int n2 = 1010101;
   ~~~

3. 八进制：0-7，满8进1，以数字0开头表示

   ~~~java
   int n3 = 01010；
   ~~~

4. 十六进制：0-9及A(10)-F(15),满16进1，以0x或0X开头表示，此处的A-F不区分大小写

   ~~~java
   int n4 = 0x10101；
   ~~~

### 进制的转换

二进制转换成十进制

![image-20240111200650802](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111200650802.png)

八进制转换成十进制

![image-20240111200816118](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111200816118.png)

十六进制转换成十进制

![image-20240111201341920](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111201341920.png)

十进制转换成二进制

![image-20240111202319146](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111202319146.png)

十进制转换成八进制

![image-20240111202410081](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111202410081.png)

十进制转换成十六进制

![image-20240111204040894](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240111204040894.png)

二进制转换成八进制

![image-20240112093415147](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112093415147.png)

二进制转换成十六进制

![image-20240112093537194](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112093537194.png)

八进制转换成二进制

![image-20240112093850765](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112093850765.png)

十六进制转换成二进制

![image-20240112094103156](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112094103156.png)

### 原码 反码 补码

![image-20240112094817593](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112094817593.png)

### 位运算符

![image-20240112095126875](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112095126875.png)

![image-20240112100539971](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240112100539971.png)