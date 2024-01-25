<h1 align = "center">Day05</h1>

### 数组

可以存放==多个同一类型==的数据，数组也是一种数据类型，是引用类型。

声明方式 ：数据类型[] 数组名 = {元素，元素}；

或者：数据类型 数组名[] = {元素，元素}；  这两个声明方式都是等价的

~~~java
//定义数组使用[],元素使用{ }，多个元素使用逗号隔开
double[] hen = {3,6,5,10.2,18,30.99};
//打印数组长度，长度是6
System.out.println("数组的元素长度是" +hen.length);
//定义一个变量来接收元素之和
double sum = 0;
//使用for循环来遍历数组元素，从0开始计算一共有五个元素，长度是六，所以可以直接和长度比较
//或者直接 i < 6;
    for (int i = 0; i < hen.length; i++){
        // sum = sum + hen[0-5],0表示第一个元素，1表示第二个元素...
        sum += hen[i];
    }
System.out.println("六只鸡总体重是" + sum + "平均体重是" + (sum / 6));
~~~

##### 数组的使用

动态初始化 ----1：

数据类型[] 数组名 = new 数据类型[大小]

~~~java
//声明一个a数组为double类型，然后可以存放5个元素
double[] a = new double[5]; 
//案例演示：
//创建5个元素大小的数组
double[] scores = new double[5];
//创建文本扫描器
Scanner myScanner = new Scanner(System.in);
//循环让用户输入成绩，并将成绩赋值给数组scores
for (int i = 0; i < scores.length; i++){
    System.out.println("请输入第" + (i + 1) + "位学生的成绩");
    scores[i] = myScanner.nextDouble();
}
//遍历数组内容
for (int i = 0; i < scores.length; i++){
    System.out.println("第" + (i + 1) + "位学生的成绩是" +scores[i]);
}
~~~

动态初始化 ----2：

先声明，后面赋值；

~~~java
double[] a;	//先声明一个空数组a
a = new double[5]; //在赋值元素空间给a
~~~

静态初始化：

~~~java
double[] hen = {3,6,5,10.2,18,30.99};
//等价于
double[] hen = new double[6];
hen[0] = 3;  hen[1] = 6;  hen[2] = 53;  hen[3] = 10.2;  hen[4] = 18;  hen[5] = 30.99;
~~~

数组使用的细节：

![image-20240118112042678](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240118112042678.png)

##### 赋值机制

变量的赋值方式是值传递/值拷贝

~~~java
int a = 20;
int b = a; // b = 20
b = 100; //现在a = 20， b = 100
~~~

数组的赋值方式是引用传递/地址拷贝

~~~java
int[] a = {20,30,5};
int[] b = a;
b[0] = 10; //将第一个下标的值改为了10，int[] b = {10,30,5};
//a数组也会改变  int[] a = {10,30,5};
~~~

![image-20240118121447159](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240118121447159.png)

那么如何将a的元素拷贝给b呢

~~~java
int[] a = {20,30,5};
//创建一个新的数组，开辟和a元素一样大的空间
int[] b = new int[a.lenght];
//遍历a，将a的每一个元素赋值给b
for(int i = 0; i < 3; i++){
    b[i] = a[i];
}
~~~

### 排序

两个两个元素依次对比，每一轮将最大或最小的数放在最后的元素位

~~~java
//定义一个数组
int[] arr = {90,88,19,-11,10,1};
//定义一个temp来接收中转
int temp = 0;
//对比的轮数等于容量大小 - 1，所有先用for循环来进行嵌套
for (int i = 0; i < arr.length -1; i++){
    //比较越来越小，总共5次比较，4次比较，3次比较...
    for (int j = 0; j < arr.length -1 - i; j++){
        //如果下标j的数大于后面的j+1下标的数，那么就将j下标的数先存放在temp
        if (arr[j] > arr[j + 1]){
            temp = arr[j];
            //再将下标大的j+1数赋值给下标j，这样小的数就在前面了
            arr[j] = arr[j + 1];
            //将存放大下标j的数据temp赋值给后面的下标j+1，这样大的数就在后面了，依次这样循环
            arr[j + 1] = temp;
        }
    }
    System.out.println("\n第" +(i+1) +"轮排序结果 ");
    for (int a = 0 ; a < arr.length; a++){
        System.out.print(arr[a] + "\t");
    }
}
~~~

查找

~~~java
Scanner myScanner = new Scanner(System.in);
String[] name = {"张三","李四","王五","老六"};
System.out.println("请输入名字查询：");
String names = myScanner.next();
int temp = -1;
for (int i = 0; i < name.length; i++){
    //string比较用equals，比较输入的名字和数组的名字是否相等
    if (names.equals(name[i])){
        System.out.println("恭喜你找到了" + names);
        System.out.println("下标是：" + i);
        //赋值
        temp = i;
        break;
    }
    }
//上面有赋值，只要没有赋值，那么就是没找到
if (temp == -1){
    System.out.println("你找的不对");
}
~~~



二维数组

定义方式（静态初始化）：

~~~java
//都可以这么声明
int[] a[] 
int[][] a
int a[][]
~~~



~~~java
//创建了一个二维数组，有3个元素
//3个元素都是一维数组，每一个一维数组都有4个元素
//每个一维数组的元素个数都可以不相等
int[][] arr = {{0,101,110,32},{1,0,-11,110},{0,341,134,11}};

~~~

动态初始化：

~~~java
//定义二维数组
int[][] arr;
//开辟空间大小
arr = new int[2][3]
~~~



原理图：

![image-20240119135942338](https://raw.githubusercontent.com/BugDaWang/image01/master/blogImg/image-20240119135942338.png)
