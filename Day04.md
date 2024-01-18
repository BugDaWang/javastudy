<h1 align = "center">Day04</h1>

### 分支控制if-else

基本语法

~~~java
if(条件判断01){
    //条件成立执行区域里面的代码
}else if(条件判断02){
    //上面的if判断如果不成立，则执行这区域的代码
    //成立则不执行else if
}... 	//可以无限嵌套else if等
 else{
     //条件判断都不成立，那就执行else
 }
    
~~~

![image-20240115162928887](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240115162928887.png)

~~~java
//案例演示（在一个大if里面判断）
if (moneys >= 1 && moneys <= 100) {	//为了让数据正常，做一个输入数据的处理，在处理条件成立内进行判断
    if (moneys == 100) {
    System.out.println("信用极好");
    }else if (moneys >= 80 && moneys <= 99.9) {
    System.out.println("信用优秀");
    }else if (moneys >= 60 && moneys < 80) {
    System.out.println("信用一般");
    }else{
    System.out.println("不及格");
    }
}else{
    System.out.println("你输入的数据异常，请重新输入（1-100.0）：");
}
~~~



多分支取反踩坑：

~~~java
boolean a = true;
if (a = false) {	//将false赋值给a，a现在是false
    System.out.println("a");	
}else if (!a) {		//取反，a = false -> a = true，true就是成立，所有输入b
    System.out.println("b");
}else{	//上面有条件成立，故else执行
    System.out.println("c");
~~~

##### 嵌套分支

在一个分支结构中又完整的嵌套了另一个完整的分支结构，里面的分支结构叫内层分支，外面的分支叫外层分支，规范就是不要嵌套超过3层（可读性不好）

基本语法

~~~java
//判断输入的成绩是否晋级	
public static void main(String[] args){
		Scanner myScanner = new Scanner(System.in);
		System.out.println("请输入您的成绩");
		double grades = myScanner.nextDouble();
		System.out.println("请输入您的性别");
		char gender = myScanner.next().charAt(0);
		if (grades >= 8.0) {
			if (gender == '男') {
				System.out.println("恭喜您晋级男子组");
			}else if (gender == '女') {
				System.out.println("恭喜您晋级女子组");
			}	
			}
		else{
			System.out.println("真遗憾您被淘汰了");
		}
	}
~~~



~~~java
//由用户输入月份，月份区分淡季旺季，来查询成人，老人，小孩的票价
public static void main(String[] args){
		Scanner myScanner = new Scanner(System.in);
		double money = 60;
		System.out.println("请输入您需要购买的月份");
		int month = myScanner.nextInt();
		if (month >= 4 && month <= 10){
			System.out.println("请输入您的年龄");
			short old = myScanner.nextShort();
			if (old >= 18 && old < 60){
				System.out.println("您是成人，票价是" + money);	
			}else if (old < 18) {
				System.out.println("由于您是儿童，票价是" + (money / 2));
			}else if (old > 60) {
				System.out.println("由于您是老人，票价是" + (money / 3));
			}
		}else if (month <=3 || (month >10 && month <=12)) {
			System.out.println("请输入您的年龄");
			short old = myScanner.nextShort();
			if (old >= 18 && old < 60){
				System.out.println("您是成人，票价是" + (money - 20));	
			}else{
				System.out.println("票价是" + (money / 2));	
			}
		}else{
			System.out.println("您输入的月份不正常，请重新输入");
		}
	}
~~~



### switch分支

基本语法

要注意，如果第一个case 匹配成功且没有break，会直接执行后面的case语句块，不会再次进行判断，这个现象叫穿透



~~~java
switch( 表达式 ){
//当表达式匹配到case 常量1时，执行语句块1，然后在执行break结束该switch
	case 常量1;
	语句块1;
	break;//是否有break，有就结束该switch，没有就执行case2中的语句块，
  		            //直到执行到有break的case或者最后的default。
//当表达式匹配到case 常量2时，执行语句块2，然后在执行break结束该switch
	case 常量2;
	语句块2;
	break;
//当表达式没有匹配到case，则执行default语句，然后在执行break结束该switch
	default:
	default语句块3
	break;
}
~~~

![image-20240116105950807](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240116105950807.png)

~~~java
//案例演示
//输入成绩来判断是否合格
class switch03 {
    public static void main(String[] args){
        Scanner myScanner = new Scanner(System.in);
        System.out.println("请输入学生成绩");
        double score = myScanner.nextDouble();
        if (score >= 0 && score <= 100){
            //double强转为int，因为switch不能为double，因为60-100合格分除以60取整都是1，则我们可以用1来判断合格不合格；
            switch ((int)(score / 60)) {
                case 1:
                    System.out.println("合格");
                    break;
                case 0:
                    System.out.println("不及格");
                    break;
                //default:
                    //System.out.println("你输入的成绩有误");
            }
        }else {
            System.out.println("你输入的成绩有误");
        }
    }
}
~~~

![image-20240116112953608](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240116112953608.png)



### for循环控制

基本语法

~~~java
for(循环变量初始化;循环条件;循环变量迭代){
    循环操作(可以多条语句);
}
//案例演示
//初始化变量i = 1，再看条件，条件为true，则执行循环操作；
//然后看i++，每循环一次则i自增1
//顺序就是赋值，判断循环条件，t执行循环操作，f不执行，执行循环操作后在进行一个迭代，迭代知道i大于10，循环条件为f
for(i = 1; i <= 10; i++){ 
    System.out.println("hello,world")
}
~~~

![image-20240116133009427](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240116133009427.png)



### while循环控制

基本语法

~~~java
循环变量初始化;
while(循环条件){
    	循环体(语句);
    	循环变量迭代; 
}
//案例演示
public static void main(String[] args){
    //初始化变量
    int start = 40;
    int end = 200;
    //循环条件
    while ( start <= end){
        if (start % 2 == 0){
            //循环执行语句
            System.out.println("40-200之间的偶数有" + start);
        }
        //循环变量迭代
        start++;
   }
}
~~~

![image-20240116150253571](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240116150253571.png)

### do..while循环

基本语法

~~~java
//先执行，在判断，一定会至少执行一次
do{
    循环体(语句);
    循环变量迭代;
}while(循环条件);
//案例演示
//200以内能被5整除不能被3整除的数
class dowhile03 {
    public static void main(String[] args){
        int num1 = 1;
        int end = 200;
        int count = 0;
        do {
            num1++;
            if (num1 % 5 == 0 && num1 % 3 !=0){
                System.out.println(num1);
                count ++;
            }
        }while (num1 <= end);
        System.out.println("有" + count +"个可以被5整除不能被3整除的数");
    }
}

//对话演示
class dowhile04 {
    public static void main(String[] args){
        Scanner myScanner = new Scanner(System.in);
        char m1 = ' ';
        do {
            System.out.println("小明使出了闪电五连鞭对他说到：");
            System.out.println("臭小子你还不还钱？？y/n");
            m1 = myScanner.next().charAt(0);
            System.out.println("臭小子的回答是" +m1);
        }while ( m1 != 'y');//t就继续执行，f跳出
        System.out.println("算你小子实相，快点把钱交出来吧");
    }
}![image-20240116153836180](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240116153836180.png)
~~~



### 多重循环控制

执行步骤分析：

~~~java
for(int i = 0; i < 2; i++){
    for(int j = 0; j < 3; j++){
        System.out.println("i=" +i +"j=" + j);
    }
}
~~~

![image-20240116165518461](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240116165518461.png)

~~~java
//统计3个班的成绩情况，每个班有5名同学，
//求出各个班的平均分和所有班级的平均分[学生的成绩从键盘输入]
//统计出三个班的及格人数，每个班有5名同学；
import java.util.Scanner;
public class Multipleloops {
    public static void main(String[] args){
        Scanner myScanner = new Scanner(System.in);
        double Scores = 0;
        int ispass = 0;
        for (int Class = 1; Class <= 3; Class++){
            double Score = 0;
            for (int schoolmate = 1; schoolmate <=5; schoolmate++){
                System.out.println("请输入第" +Class +"年级第" + schoolmate +"同学的成绩:");
                double grades = myScanner.nextDouble();
                if (grades >= 60){
                    ispass++;
                }
                System.out.println("成绩是:" + grades);
                Score += grades;
            }
            Scores += Score;
            System.out.println("第" + Class +"年级总分成绩是:" + Score +"平均分是" +(Score /5));
        }
        System.out.println("所有年级总分是：" + Scores + "平均分是：" + (Scores / 15));
        System.out.println("全年级及格人数有" + ispass);
    }
}
~~~



### 跳转控制语句-break

![image-20240117095309356](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240117095309356.png)

~~~java
public static void main(String[] args){
    for(int i = 0; i < 10; i++){
        if ( i == 3){
            break;  //只要i++后等于3，那么执行break跳出整个for循环继续执行下面的语句
        }
        System.out.println("i=" +i);
    }
~~~

break标签的使用

标签可以自定义名字

~~~java
class bleak2 {
    public static void main(String[] args){
        for(int i = 0; i < 10; i++){
            lable1:
                if ( i == 3){
                    System.out.println("i = " + i + "时我就结束lable1");
                break lable1;  //标签可以自定义，break标签后，这段标签的循环结束，执行剩余的循环或代码；
            }
            System.out.println("i=" +i);
        }
        System.out.println("程序继续执行...");
    }
}

//登录案例演示
Scanner myScanner = new Scanner(System.in);
int chance = 3;
for (int i = 1; i <= 3; i ++){
    System.out.println("请输入用户名进行登录");
    String name = myScanner.next();
    System.out.println("请输入密码进行登录");
    int password = myScanner.nextInt();
    if ("丁真".equals(name) && password == 666){
        System.out.println("登录成功");
        break;
    }else {
        System.out.println("登录失败，用户名或密码错误");
        chance--;
    }
    System.out.println("你还有" +chance +"次机会");
}
~~~



### 跳转控制语句-continue

结束当前的循环，继续执行下一次循环；

~~~java
int i = 1;
while (i <= 4 ){
    i++;
    if( i == 2){
        continue; //结束if循环，继续while循环
    }
    System.out.println("i = " +i);
}
~~~

![image-20240117153023643](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240117153023643.png)



### 跳转控制语句-return

使用在方法，表示跳出所在方法，注意，如果return写在main方法，则会退出程序

~~~java
public static void main(String[] args){
    int i = 1;
	while (i <= 4 ){
    i++;
   		 if( i == 2){
        return; //跳出这个main方法
   		 }
    System.out.println("i = " +i);
	}
}

~~~

