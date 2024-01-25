<h1 align = "center">Day06</h1>

### 类与对象

先定义类->自定义数据类型 ->实例化

##### 类：

类是抽象的，概念的，代表一类事物，比如人类猫类...即它是数据类型。

~~~java
例如案例里面的cat cat01 = new cat();
~~~

##### 对象：

对象是具体的，实际的，代表一个具体的事物，即是 实例。

类是对象的模板，对象是类的一个个体，对应一个示例。

~~~java
例如案例里面的 cat cat01 = new cat(); cat cat02 = new cat();
~~~

~~~java
//第二步就是实例化对象
//实例化第一只猫[创建一只猫对象]
//new cat()创建一个对象空间，将空间赋值给赋值给car01
//实际中，new cat();创建的对象空间，才是真正的对象
//而cat01是对象名（对象引用）
cat cat01 = new cat();
cat01.name = "小白";
cat01.age = 17;
cat01.color = "白色";
//实例化第二只猫
cat cat02 = new cat();
cat02.name = "小蓝";
cat02.age = 20;
cat02.color = "蓝色";
}
}
//第一步先创建类型，在定义猫的属性
class cat{
//猫的属性，也叫成员变量、字段、field
//属性可以是基本数据类型或引用类型（对象，数组）
//注意基本数据类型如果没有赋值，那就会有默认值
String name;
int age;
String color;
}
~~~

对象内存分析图：

![image-20240120141125819](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240120141125819.png)

创建对象可以先声明在创建

~~~java
//先声明在创建
cat cat01; //声明对象cat01
cat01 = new cat(); //创建
//直接创建
cat cat01 = new cat();
~~~



### 方法

方法写在类的里面，如果写完方法后没有去调用（使用），则不会输出

调用方法就是先创建一个对象然后再去使用这个方法

方法的定义：

~~~java
访问修饰符 返回的数据类型 方法名(形参列表...){ //方法体
    语句;
    return 返回值;
}
~~~

~~~java
//案例演示
public class Mothod01 {
    public static void main(String[] args){
        //在foundation实例化对象p1
        foundation p1 = new foundation();
        p1.speak();//调用方法spea
        p1.cal01(1000);//调用cal01方法，输入形参1000
        //用户输入100，200，表示将100赋值给num1，将250赋值给num2
        //把赋值计算后的和返回，用sums接收
        int sums = p1.cal02(100,250);
        System.out.println("使用cal02方法计算的和是：" + sums);
        //在MyTools实例化对象p2
        MyTools p2 = new MyTools();
        //创建一个二维数组
        int[][] arr = {{1,2,0},{0,8,19},{0,0,0}};
        //调用printarr方法，形参输入这个二维数组
        p2.printarr(arr);

    }
}
class foundation{
    //public: 的意思是表示方法的公开
    //void: 表示没有返回值
    //speak(): 是方法名，方法名可以自定义,()表示形参列表
    //{}: 方法体,可以写我们需要执行的代码
    public void speak(){
        System.out.println("调用的speak方法输出的一句话阿巴阿巴阿巴");
    }
    //创建一个方法cal01，并接收一个用户输入的形参算出它们的和
    //形参在调用的时候使用
    //循环求出1 到 用户输入的数之和
    public void cal01(int n){
        int sum = 0;
        for (int i = 1; i <= n; i++){
            sum += i;
        }
        System.out.println("使用cal01方法计算1到" + n +"的和是：" + sum);
    }
    //求出两个数的和
    //创建方法cal02，int表示方法执行后，会返回一个int值
    //(int num1,int num2)表示需要接收用户输入的两个形参，之间需要用逗号隔开
    //return sum,表示将sum的值返回
    public int cal02(int num1,int num2){
        int sum = num1 + num2;
        return sum;
    }
}

//遍历二维数组方法
class MyTools{
    //形参接收一个二维数组，名字任意
    public void printarr(int[][] xingcan){
        for (int i = 0; i < xingcan.length; i++){
            for (int j = 0; j < xingcan[i].length; j++){
                System.out.print(xingcan[i][j] + " ");
            }
            System.out.println();
        }
    }
}
~~~

一个方法最多只有一个返回值，但是我们可以使用数组来接收

```java
public class Mothod01 {
    public static void main(String[] args){
        //在AA类中实例化a
        AA a = new AA();
        //输入形参然后以数组的形式赋值给res，必须要数组接收，因为返回的也是数组
        int[] res = a.getSumAndSub(90,80);
        System.out.println("他们的和是" + res[0]);
        System.out.println("他们的差是" + res[1]);
    }
}

class AA{
    //先创建一个getSumAndSub方法，使用数组方式返回
    public int[] getSumAndSub(int n1,int n2){
        //开辟空间给arr数组
        int[] arr = new int[3];
        //使用arr数组的第一个元素来接收和
        arr[0] = n1 + n2;
        //使用arr数组的第二个元素来接收差
        arr[1] = n1 - n2;
        return arr;
    }
}       
```

使用细节图：

![image-20240123174130610](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240123174130610.png)

跨类直接调用

~~~java
//跨类直接调用方法，和public权限有关系
b bb = new b();
bb.b1();

//跨类直接调用
class b{
    public void b1(){
        c cc = new c();
        cc.c1();
        //第二执行这句输出语句
        System.out.println("调用b1()方法");
    }
}
class c{
    public void c1(){
        //第一执行这句输出语句
        System.out.println("调用c1()方法");
    }
}
~~~



### 递归

看图解析：

```java
public class recursion01 {
    public static void main(String[] args){
        A a1 = new A();
        a1.test01(10);
    }
}
class A{
    public void test01(int n){
        if (n > 2){
            test01(n - 1);
        }
        System.out.println("n=" + n);
    }
}
```

![image-20240124143310464](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240124143310464.png)

![image-20240124144013420](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240124144013420.png)



### 重载

```java
public class heavyload01 {
    public static void main(String[] args){
        MyCalculator mc = new MyCalculator();
        //输出
        System.out.println(mc.calculate(1.1,2));
    }
}
class MyCalculator{
    //创建多个相加的同名方法进行重载匹配，最后使用print输出
    public int calculate(int n1,int n2){
        return n1 + n2;
    }
   public int calculate(double n1,int n2){
        return n1 + n2;
    }
    public double calculate(int n1,double n2){
        return n1 + n2;
    }
    public int calculate(int n1,int n2,int n3){
        return n1 + n2 + n3;
    }
}
```

注意细节

1. 方法名必须相同

   ~~~java
   //错误演示
   public int calculate01
   public int calculate02
   ~~~

2. 形参列表必须不同（形参个数，类型或顺序至少一个不一样）

   ~~~java
   //错误演示
   public double calculate(int n1,double n2)
   public int calculate(int n1,double n2)
   ~~~

3. 没有返回类型要求



### 可变参数

将==同一个类==中的==同功能==但==参数个数不同==的方法，封装为一个方法，就可以通过可变参数来实现。

##### 基本语法

访问修饰符 返回类型 方法名(数据类型==...==形参名){ }

~~~java
public class Variadics01 {
    public static void main(String[] args){
    method01 m = new method01();
    System.out.println("和等于：" + m.sumss(1,2,3,4,5,5));
    }
}
class method01{
    //int... 表示的是可接收多个可变参数，类型是int，范围是int（0-多）
    //使用可变参数时，可以当作数组来使用，即将nums 当作数组
    //遍历nums求和
    public int sumss(int... nums){
        int res = 0;
        for (int i = 0;i<nums.length;i++){
         res += nums[i];
        }
        return res;
    }
}
~~~

##### 注意事项和使用细节

可变参数可以是0个或者多个

可变参数的实参可以为数组

可变参数的本质就是数组

可变参数可以和普通类型参数放在形参列表上，但是可变参数一定要在最后

~~~java
//创建方法a，形参中有多个数据类型，要将可变参数放到最后
public void a(String str, double... nums)
~~~

一个形参列表中只可以出现一个可变参数



### 作用域

==局部变量==存在一个方法中，作用域就是只能在这一个方法中去使用，必须要赋值

==全局变量==也就是属性，它的作用域为整个类或其他类来使用，且可以不赋值

```java
class cat01{
    //全局变量，在这个类中可以随便调用这个属性
    //全局变量可以是空，不赋值，因为有默认值
    int n1 = 11;
    public void n1(){
        //局部变量一般指在成员方法中定义的变量
        //n2 和 name就是局部变量
        //n2 和 name的作用域只在n1方法中
        //局部变量不能为空，为空编译不过去，会说数据未初始化，就是没赋值
        //所以局部变量必须赋值
        int n2 = 10;
        String name = "小橘";
    }
}
```

![image-20240125121438201](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240125121438201.png)



### 构造器

1. 构造器的修饰符可以是默认，也是可以public，protected，private

2. 构造器==没有返回值==，也不能写==void==

3. ==方法名和类名字必须一样==

4. 参数列表和成员方法一样的规则

5. 构造器的调用，由系统完成



### this关键字的使用

哪个对象在调用，this就代表哪个对象； 

```java
public class this01 {
    public static void main(String[] args){
        //创建对象并且直接赋值给构造器
        dog d1 = new dog("旺财",10);
        d1.info();
    }
}
class dog{
    //创建几个属性，name和age
    String name;
    int age;
    //创建构造器
    public dog(String name,int age){
        //this.name就是当前对象的的属性name，这个this就是最上面new出来的对象
        this.name = name;
        //this.age就是当前对象的的属性age
        this.age = age;
    }
    public void info(){
        System.out.println("名字是：" + name  + "\t" + "年龄是：" + age);
    }
}
```

使用细节：

![image-20240125204729400](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240125204729400.png)
