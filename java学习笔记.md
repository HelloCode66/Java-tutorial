# Java基础

## Java基础语法

### 前期准备

1. **环境搭建**(https://www.java.com/zh-CN/)

   - 了解JRE和JDK

   - JDK的下载和安装

2. **常用DOS命令**

   ![](images\常用DOS命令.png)

3. **第一个Java程序**

   ![](images\第一个java程序.png)

   ```java
   public class Hello{									//定义一个名为Hello的类（
       public static void main(String[] args){			//main入口
           System.out.println("Hello World");			//打印输出Hello World
       }
   }
   ```

   

### 数据类型



1. **常量**：在程序的执行过程中，其值不会发生改变的量（数据）。

![](images\常量.png)

2. **变量**：就是内存中的==存储空间==，空间中存储着经常发生改变的值。

![](images\变量.png)

3. **基本数据类型**

![](images\基本数据类型.png)

4. **引用数据类型**

### 键盘录入

1. **目的**：为了让数据更加灵活
2. **步骤**
   
   * 导包：`import java.util.Scanner;`		(需要写在class上面)
   * 创建对象：`Scanner sc = new Scanner(System.in);`        (只有sc可以改变，其他属于固定格式)
   * 使用变量接收数据:`int i = sc.nextInt();`			(只有i和sc变量可以改变，其他属于固定格式)
   
3. **实例**

   ```java
   import java.util.Scanner;	//导包
   public class input{		//创建input类
       public static void main(String[] args){		//主入口
           Scanner scan = new Scanner(System.in);	//创建对象
           int a = scan.nextInt();		//使用变量接收数据
           System.out.println(a);		//打印输出数据
       }
   }
   ```

### 标识符

1. **标识符**：就是给类、方法、变量等起名字的符号
2. **定义规则**
   
   * 由==数字==、==字母==、==下划线==(_)和==美元符==($)组成。
   * 不能以数字开头
   * 不能是关键字
   * 严格区分大小写
   
3. **常见命名约定**

   - 小驼峰命名法：==方法==、==变量==

     约定1：标识符是一个单词的时候，首字母小写
     范例1：`name`
     约定2：标识符由多个单词组成的时候，第一个单词首字母小写，其他单词首字母大写
     范例2：`firstName`

   - 大驼峰命名法：==类==

     约定1：标识符是一个单词的时候，首字母大写
     范例1：`Student`
     约定2：标识符由多个单词组成的时候，每个单词首字母都大写
     范例2：`GoodStudent`

### 类型转换

1. **隐式转换**：将数据类型中，==取值范围小的==数据，==给取值范围大的==类型赋值，可以直接赋值

   ```java
   int a = 10;		//int占4字节
   double b = a;	//double占8字节
   ```

   > 简单记：小的给大的，可以直接给
   > 4升的油，倒入8升的桶，可以直接倒入
   > 小的数据和大的数据类型运算，小的会先提升为大的数据类型再进行运算
   > byte short char 这三种数据在运算的时候，无论是否有更高的数据类型，都会提升为int，然后再进行运算

   ![](E:\Typora\学习笔记\images\隐式转换.png)

2. **强制转换**：把一个表示==数据范围大==的数值或者变量赋值给另一个表示==数据范围小的变量==
   格式：目标数据类型 变量名 = (目标数据类型)值或者变量;

   ```java
   int a = 10;		//int 4字节
   byte b = (byte)a;		//byte 1字节
   int c = (int)88.88;
   ```

   > 强制类型转换，有可能会发生精度损失
   > 精度损失：简单理解，将容积为8升的水倒入容积为4升的桶中，多出的水会洒掉

3. **类型转换案例**

   * 请判断下列代码是否存在问题，如果有，请指出并改正[^1.51][^1.52]

     ```java
     public class Test{
         public static void main(String[] args){
             byte a = 3;			//①
             byte b = 4;			//②
             byte c = a + b;		//③
             byte d = 3 + 4;		//④
         }
     }
     ```

[^1.51]: ③中错误，在byte short char运算时，会直接提升为int，然后再进行运算;
[^1.52]: ④正确：Java存在常量优化机制，3和4是两个常量，会在编译的时候让3和4进行相加，然后判断7是否在byte的取值范围内

### 运算符

1. **运算符**：对常量或者变量进行操作的符号

2. **表达式**：用运算符把常量或者变量连接起来符合Java语法的式子就可以称为表达式。
   	          不同运算符连接的表达式体现的是不同类型的表达式。

   ```java
   int a = 10;
   int b = 20;
   int c = a + b; 
   ```

3. **算术运算符**：加（+）、减（-）、乘（*）、除（/）、取余（%）
   加、减、乘都和小学一样，在用除法时，两整数相除只能得到整数，想要得到小数必须有==浮点数==参与运算
   取余即指取结果的余数

> 字符之间相加时，字符会根据ASCII码值提升为int类型进行运算	（0--48   a--97   A--65）

```java
int a = 1;
char b = 'a';
System.out.println(a + b);		//输出98
```

> 字符串之间相加时，可以使用+和（任意数据类型）拼接
> 当‘+’操作中出现字符串时，这个‘+’是字符串连接符，而不是算术运算符
> 在‘+’操作中，如果出现了字符串，就是连接运算符，否则就是算术运算符，当连续进行‘+’操作时，从左到右逐个执行

```java
System.out.println("java" + 666);		//java666
System.out.println(1 + 99 +"java");		//100java
System.out.println("5+5=" + 5 + 5);		//5+5=55
System.out.println("5+5=" + (5 + 5));	//5+5=10
```

4. **自增自减运算符**：自增（++）、自减（--）
   *  ==单独使用时==，++和--在前或者在后时结果都一样
   * 当参与其他操作时，在前则==先==自增（自减）==后==进行操作；在后则表示==先==进行相应操作==后==进行自增（自减）
   * ==只能操作变量，不能操作常量==

5. **赋值运算符**：赋值(=)、加后赋值(+=)、减后赋值(-=)、乘后赋值(*=)、除后赋值(/=)、取余后赋值(%=)

   ```java
   int a = 10;
   a += 20;	//a = a + 20
   System.out.println(a);		//30
   ```

   ==注意==：扩展运算符底层会自带强制类型转换的功能

6. **关系（比较）运算符**：等于(\==)、不等(!=)、大于(>)、大于等于(>=)、小于(<)、小于等于(<=)
   ==注意==：返回结果只有==true==或者==false==

7. **逻辑运算符**

   * &（与）：并且，全真则真，一假则假

   * |（或）：或者，全假则假，一真则真

   * !（非）：取反，真假假真

   * ^（异或）：两同为假，不同为真

   * 短路逻辑运算符

     &&(短路与)：作用和&相同，但有短路效果

     ||(短路与)：作用和|相同，但有短路效果

     > ​	逻辑短路：&&遇到false直接为false,不执行后面代码;||遇到true则直接为true，不执行后续代码

8. **三元运算符**

   * 格式：`关系表达式 ? 表达式1 : 表达式2;`

   * 执行流程

     首先计算==关系表达式==的值
     若为==true==则取表达式1的值
     若为==false==则取表达式2的值

### 流程控制

1. **流程控制语句**：通过一些语句，来控制程序的执行流程

2. **顺序结构语句**：程序中最简单最基本的流程控制，没有特定的语法结构，按照代码的先后顺序依次执行，程序中大多数代码都是这样的

3. **if语句**

   - 格式1：

     ```java
     if(关系表达式){
         语句体1；
     }else{
         语句体2;
     }
     ```

   - 执行流程：
     首先计算关系表达式的值
     如果关系表达式的值为true则执行语句体1
     如果关系表达式为false就执行语句体2
     继续执行后续代码

     ```java
     import java.util.Scanner;
     public class a{
     	public static void main(String[] args){
     		Scanner sc = new Scanner(System.in);
     		System.out.println("请输入您的年龄：");
     		int age = sc.nextInt();
     		if(age >= 18){
     			System.out.println("您已成年，可以进入");
     		}else{
     			System.out.println("对不起，您未成年，不能进入");
     		}
     	}
     }
     ```

     > 如果if语句中的语句体只有一条，那么大括号{}可以省略不写，但是不建议，容易混淆
     > if语句小括号后面不要写分号;

   - 格式2(多条件判断)：

     ```java
     if(判断条件){
         语句体1;
     }else if(判断条件2){
         语句体2;
     }
     ...
     else{
         语句体n+1;
     }
     ```

     ```java
     import java.util.Scanner;
     
     public class a{
     	public static void main(String[] args){
     		Scanner sc = new Scanner(System.in);
     		System.out.println("请输入您的成绩：");
     		int score = sc.nextInt();
     		if(score >= 90 && score <= 100){
     			System.out.println("优秀");
     		}else if(score >= 80 && score < 90){
     			System.out.println("良好");
     		}else if(score >=60 && score < 80){
     			System.out.println("及格");
     		}else if(score <60 && score >= 0){
     			System.out.println("不及格");
     		}else{
     			System.out.println("请输入正确的成绩！");
     		}
     	}
     }
     ```

   4. **switch语句**

      - 格式：

      ```java
      switch(表达式){
          case 值1:
              语句体1；
              break;
          case 值2;
              语句体2;
              break;
          ....
          default:
              语句体n+1;
              break;
      }
      ```

      - 格式说明:

        表达式==（将要被匹配的值）==取值为byte、short、int、char、JDK5、以后还可以是枚举，JDK7以后可以是String
        case:后面跟的是要和表达式比较的值==（被匹配的值）==
        break：表示中断，结束的意思，用来结束switch语句
        default：表示所有的情况都不匹配的时候，就执行该处的内容，和if语句的else相似

      - case穿透：

        现象：当开始case穿透，后续的case就不会具有匹配的效果，内部的语句都会执行

        ​			直到看见break，或者将整体switch语句执行完毕，才会结束
        应用场景：当多个case语句出现重复现象，就可以考虑使用case穿透来优化代码

   5. **for循环**（推荐明确循环次数时使用）

      - 格式：

        ```java
        for(初始化语句;条件判断语句;条件控制语句){
            循环体语句;
        }
        ```

      - 执行流程：
        执行初始化语句
        执行条件判断语句，看其结果是true还是false
                如果是false，循环结束
                如果是true，循环继续
        执行循环体语句
        执行条件控制语句
        回到第2步继续循环

      - 案例

        ```java
        //在控制台输出1-5
        for(int i = 1;i <= 5;i++){
            System.out.println(i);
        }
        ```
        
        ```java
        //求1-5的数据和
        int sum = 0;
        for(int i = 1;i <= 5;i++){
            sum += i;
        }
        System.out.println(sum);
        ```
        
        ```java
        //求1-100的偶数和
        int sum = 0;
        for(int i = 1;i <= 100;i++){
            if(i % 2 == 0){
                sum += i;
            }
        }
        System.out.println(sum);
        ```
        
        ```java
        //输出所有的水仙花数
        //水仙花数：是一个三位数，个位、十位、百位的数字立方和等于原数
        for(int i = 100;i <= 999;i++){
            int sum;
            int a = i % 10;
            int b = i / 10 % 10;
            int c = i / 100;
            sum = a * a * a + b * b * b + c * c * c;
            if(sum == i){
                System.out.println(i);
            }
        }
        ```
        
        > System.out.print()为同行打印，不换行
        > System.out.println()自带换行效果，类似于html中的块级元素，独占一行。括号内无内容时可以当作换行符来使用
   
6. **while循环**(不明确循环次数时推荐while)

   - 格式：

     ```java
     while(条件判断语句){
         循环体语句;
         条件控制语句;
     }
     ```

     ```java
     int i = 1;
     while(int i <= 100){
         System.out.println(i);
         i++;
     }
     ```

7. **do...while循环**（使用较少）

   - 格式：

     ```java
     do{
         循环体语句;
         条件控制语句;
     }while(条件判断语句);
     ```

   > **三种循环的区别：**
   > for循环和while循环先判断条件是否成立，然后决定是否执行循环体（先判断后执行）
   > do...while循环先执行一次循环体，然后判断条件是否成立，是否继续执行循环体（先执行后判断）
   > 条件控制语句中所控制的自增变量，因为归属于for循环的语法结构中，在for循环结束后，就==不能再次被访问==到了
   > 条件控制语句所控制的自增变量，对于while循环来说不归属其语法结构中，在while循环结束后，该变量==还可以继续使用==

6. **死循环**

   ```java
   //for
   for(;;){
       循环体语句;
   }
   //while
   while(true){
       循环体语句;
   }
   //do...while
   do{
       循环体语句;
   }while(true);
   ```

   - 应用场景：

   ​	例如：键盘录入一个1-100之间的整数（用户可能出现误操作现象）

   ```java
   while(true){
       Scanner sc = new Scanner(System.in);
       int a = sc.nextInt();
       if(a >= 1 && a <= 100){
           b
       }
   }
   ```

7. **continue与break关键字**
   - continue：跳过某次循环内容，继续开始下一层循环，只能在循环中使用
   
   - break：跳出整个循环，终止循环体内容的执行，只能在循环和switch中使用
   
   - 标号：可以给语句块加标号赋予它们名称，标号位于语句之前。标号只能被continue和break引用。
   
     ```java
     public class Test{
         public static void main(String[] args){
             int n = 1;
             lo:				//标号
             while(true){
                 switch(n){
                     case 1:
                         System.out.println("1");
                         break lo;			//通过标号，这里的break将结束外层while循环
                 }
             }
         }
     }
     // 语句前只允许加一个标号，标号后面不能跟大括号。通过用break后加标号对处于标号中的语句进行控制。往往标号后是for.while.do-while等循环。
     ```

### Random

- **作用**：用于产生一个随机数

- **使用步骤**

  1. 导包

     ```java
     import java.util.Random;
     ```

  2. 创建对象

     ```java
     Random r = new Random();
     ```

  3. 获取随机数

     ```java
     int number = r.nextInt(10);		//获取数据的范围:[0,10)，包括0，不包括10
     int number = r.nextInt(10) + 1;		//获取数据的范围:[1,10]，包括1，也包括10
     ```

- **猜数字案例**

  ```java
  import java.util.Random;
  import java.util.Scanner;
  public class a{
      public static void main(String[] args){
          Random r = new Random();
          int ran = r.nextInt(100) + 1;
          while(true){
              System.out.print("请输入您猜的数字：");
              Scanner sc = new Scanner(System.in);
              int n = sc.nextInt();
              if(n > ran){
                  System.out.println("猜大了~~");
              }else if(n < ran){
                  System.out.println("猜小了~~");
              }else {
                  System.out.println("猜恭喜你，猜对了，答案就是" + ran);
                  break;
              }
          }
      }
  }
  ```

### 开发神器-IDEA

- **概述**：IDEA全称==IntelliJ IDEA==，是用于Java语言开发的集成环境，它是业界公认的目前用于Java程序开发最好的工具

  **集成环境**：就是把代码编写、编译、执行、调试等多种功能综合到一起的开发工具

- **下载和安装**

  下载：<https://www.jetbrains.com/idea/>

  安装：傻瓜式安装，建议修改安装路径

- **IDEA项目结构**

  project-module-package-class
  这些结构的划分，是为了方便管理文件

- **IDEA中的第一个代码**
  
  1. 创建Project项目
  2. 创建Module模块
  3. 创建Package包
  4. 创建Class类
  5. 在类中编写代码
  6. 完成编译运行

> 注意：最后代码一定要存放到src目录下，包名类似于com.baidu.demo1这样的格式

- **常用快捷键**
  1. psvm + 回车：快速生成main方法
  2. sout + 回车：快速生成输出语句
  3. alt + 1 ：快速打开\隐藏工程目录结构
  4. alt + 4：打开\隐藏控制台
  5. Ctrl + alt + l：格式化代码
  6. alt + 回车：代码修正提示
  7. ctrl + D：向下复制一行
  8. ctrl + X：剪切当前行
  9. Ctrl + /：批量加入单行注释，再按一次就是取消注释
  10. Ctrl + shift + /：批量加入多行注释，再按一次就是取消
  11. ctrl + shift + ↑：上移当前行
  12. ctrl + shift + ↓：下移当前行
  13. Ctrl + alt + m : 将选中代码封装为一个方法
  14. 数组名.fori + 回车：快速遍历指定数组
  15. 集合.fori + 回车：快速遍历指定集合

### 数组

1. **数组（array）**：是一种容器，用来存储==同种==数据类型（或者比它所占字节小的）的多个值

2. **格式**

   ```java
   //1.数据类型[] 变量名		【最常用】
   int[] array;
   
   //2.数据类型 变量名[]		
   int array[];
   ```

3. **初始化**：Java中的数组必须先初始化，才能使用
   所谓初始化，就是在内存中，为数组容器开辟空间，并将数据存入容器的过程

   - 动态初始化：初始化时只指定数组长度，由系统为数组分配初始值（只明确元素个数，不明确具体数值，推荐使用）

     格式：`数据类型[] 变量名 = new 数据类型[数组长度];`
     范例：`int[] arr = new int[3];`
     注意：打印数组变量名，输出的是数组在内存中的地址值

4. **数组元素访问**
   数组内存地址的访问：`数组名`
   数组内部保存的数据的访问：`数组名[索引]`
   索引从0开始，连续的，逐一增加
   数组在创建完毕后，没有赋值也能取出，取出的值为0
   默认值：
        整数——0
        浮点数——0.0
        布尔——false
        字符——空字符
        引用数据类型——null

5. **内存分配**
   Java程序在运行时，需要在内存中分配空间
   为了提高效率，就对空间进行了不同区域的划分
   每一片区域都有特定的处理数据的方式和内存管理方式
   栈内存：方法运行时，进入的内存，局部变量都存放于这块内存当中
   堆内存：new出来的内容就会进入堆内存，并且会存在地址值

   方法区：字节码文件加载时进入的内存
   本地方法栈：调用操作系统相关资源
   寄存器：交给CPU去使用

6. **静态初始化**：初始化时，就可以指定数组要存储的元素，系统还会自动计算出该数组的长度（需求中明确了具体数据，直接静态初始化即可）

   格式：`数据类型[] 变量名 = new 数据类型[]{数据1,数据2,数据3,....};`
   范例：`int[] arr = new int[]{1,2,3};`
   简化格式：`int[] arr = {1,2,3};`

7. **数组遍历**：将数组中所有的元素取出来
   动态获取数组元素个数：`数组名.length`

   ```java
   int arr = {1,2,3,4,5,6,7,8,9};
   for(int i = 0; i <= arr.length; i++){
       System.out.println(arr[i]);
   }
   ```

   ==注意==：遍历是指取出数据的过程，==不要==局限的理解为：遍历就是打印

8. **数据常见操作**

   - 获取最值
     思路：定义一个变量，用于保存最大值（或最小值）
     			取数组中的第一个值作为变量的初始值（假设第一个值就是最大（小）值）

     ​			与数组中的剩余数据逐个对比

     ```java
     int[] arr = {1, 2, 3, 4, 5, 6, 7000, 8, 919};
     int max = arr[0];
     for(int i = 0; i < arr.length; i++){
         if(arr[i] > max) max = arr[i];
     }
     System.out.println("最大值为：" + max);
     ```

   - 数组元素求和

     ```java
     import java.util.Scanner;
     public class test{
         public static void main(String[] args){
             Scanner sc = new Scanner(System.in);
             int[] arr = new int[];
             int sum = 0;
             for(int i = 0; i < arr.length; i++){
                 System.out.print("请输入第" + (i+1) + "个数值：");
                 int n = sc.nextInt();
                 sum += n;
             }
             System.out.println("数组内的元素的和为：" + sum);
         }
     }
     ```

   - 数组基本查找

     ```java
     int[] arr = {19, 28, 37, 46, 50};
     Scanner sc = new Scanner(System.in);
     System.out.print("请输入您要查找的数据：");
     int n = sc.nextInt();
     for(int i = 0; i < arr.length; i++){
         if(arr[i] == n){
             System.out.println("您要查找的数据索引为：" + i);
             break;
         }
     }
     ```

     

### 方法

- **概念**：方法就是一段具有独立功能 的代码块，不调用就不执行

- **使用前提**：

  方法必须==先创建才可以使用==，该过程称为方法的定义
  方法创建后并不是直接运行的，需要手动使用后才执行，该过程称为方法调用

- **方法定义**：

  ```java
  public static void 方法名(){
      //方法体
  }
  ```

- **方法调用**：`方法名();`

  > 注意：方法必须先定义后调用，否则程序将会报错
  > 			方法与方法之间是平级关系，不能嵌套定义
  > 			在方法没有被调用的时候，都在方法区中的字节码文件（.class）中存储
  > 			方法被调用的时候，需要进入到栈内存中运行

- **带参方法的定义和调用**

  ```java
  public static void 方法名(参数){
      //方法体
  }
  ```

  单个参数：`数据类型 变量名`
  多个参数：`数据类型 变量名1 , 数据类型 变量名2 , .....`
  调用：`方法名(参数);`
  			`方法名(变量名/常量值);`
  			`方法名(变量名1/常量值1 , 变量名2/常量值2 , ...);`

  > 方法调用时，参数的数量与类型必须与方法定义中的设置相匹配，否则程序将会报错
  >
  > 

- **形参和实参**
  形参：全称形式参数，是指方法定义中的参数
  实参：全称实际参数，是指方法调用中的参数

- **带参数方法练习**

  ```java
  // 需求：设计一个方法（print）用于打印n到m之间的所有的奇数
  public class a{
      public static void main(String[] args){
          print(10, 20);
      }
      public static void print(int n, int m){
          for(int i = n; i <= m; i++){
              if(i % 2 != 0) System.out.println(i);
          }
      }
  }
  ```

- **带返回值方法的定义和调用**

  ```java
  public static 数据类型 方法名(参数){
      return 数据;
  }
  ```

  > 方法定义时，return后面的返回值与方法定义上的数据类型要匹配，否则就会报错
  > 在执行代码时，return语句后面的语句都不会执行，属于无效代码
  > `return;`可以用于结束方法，也就是方法从栈内存中弹出去，该过程称为方法的弹栈

  调用：`数据类型 变量名 = 方法名(参数);`

- **方法通用格式**

  ```java
  public static 返回值类型 方法名(参数){
      方法体;
      return 数据;
  }
  ```

- **方法重载**：

  > 方法名相同，参数也完全相同，称为方法的重复定义，是一种冲突性的错误
  > 在调用方法的时候，Java虚拟机会通过参数的不同来区分同名的方法

  在同一个类中，定义了多个==同名的方法==，但每个方法具有==不同的参数类型==或==参数个数==，这些同名的方法，就构成了重载关系
  ==注意==：识别方法之间是否是重载关系，只看方法名和参数，和返回值无关

  ==好处==：不用记忆过多繁琐的方法名字

- **方法重载练习**

  ```java
  // 需求：使用方法重载思想，设计比较两个整数是否相同的方法，兼容全整数类型(byte,short,int,long)
  public static void main(String[] args){
      System.out.println(compare(20, 30));
  }
  public static boolean compare(byte a, byte b){
      return a == b;
  }
  public static boolean compare(short a, short b){
      return a == b;
  }
  public static boolean compare(int a, int b){
      return a == b;
  }
  public static boolean compare(long a, long b){
      return a == b;
  }
  ```

- **方法的参数传递**

  1. 当传入基本数据类型时，传入的是具体的数值，且方法中的变量和main中的变量并无联系
  2. 当传入引用类型时，传入的是具体的内存地址，这种情况可以在方法中改变引用类型变量的值

- **案例**

  ```java
  // 需求：设计一个方法用于数组遍历，要求遍历的结果是在一行上的。例如：[11,22,33,44,55]
  public static void main(String[] args) {
          int[] arr = {11, 22, 33, 44, 55};
          printArray(arr);
  }
  public static void printArray(int[] arr) {
       System.out.print("[");
       for (int i = 0; i < arr.length; i++) {
          System.out.print(arr[i]);
          if (i == arr.length - 1) System.out.print("]");
          else {
             System.out.print(", ");
          }
       }
  }
  ```

  ```java
  // 需求：设计一个方法用于获取数组元素中的最大值
  public static void main(String[] args){
      int[] arr = {11,33,44,88,22};
      System.out.println("数组中的最大值为：" + max(arr));
  }
  public static int max(int[] arr){
      int max = arr[0];
      for(int i = 0; i < arr.length; i++){
          if(arr[i] > max) max = arr[i];
      }
      return max;
  }
  ```
  
  ```java
  // 需求：设计一个方法，该方法中能够同时获取最大值和最小值
  public static void main(String[] args){
      int[] arr = {11,22,33,44,2,2393,55};
      int[] res = get(arr);
      System.out.println("最大值为：" + res[0]);
      System.out.println("最小值为：" + res[1]);
  }
  public static int[] get(int[] arr){
      int max = arr[0];
      int min = arr[0];
      for(int i = 0; i < arr.length; i++){
          if(arr[i] > max) max = arr[i];
          if(arr[i] < min) min = arr[i];
      }
      int[] arrMaxAndMin = {max, min};
      return arrMaxAndMin;
  }
  ```
  
  ==注意==：return语句只能同时返回一个值，需要返回多个值的话可以使用数组

### Debug

- **概述**：是供程序员使用的程序调试工具，它可以用于==查看程序==的==执行流程==，也可以用于追踪程序执行过程来调试程序
- **操作流程**：Debug调试，又称为断点调试，断点其实是一个标记，告诉Debug从标记的地方开始查看
  添加断点 -> Debug运行 -> 根据Debug窗口调试(Step into向下进行；Stop停止) -> 删除断点

### 进制

- **进制**：指进位制：是人们规定的一种进位方式

- **常见进制**：二进制、八进制、十进制、十六进制
  计算机数据在底层运算的时候，都是以==二进制==进行的，了解不同的进制，便于我们对数据的运算过程理解的更加深刻

- **十进制**：逢十进一，借一当十

- **二进制**：逢二进一，借一当二（只有0和1）

- **八进制**：逢八进一，借一当八（0，1，2，3，4，5，6，7）

- **十六进制**：0\~9，a\~f（其中a\~f表示10~15）

  >在Java中，数值默认都是==十进制==，不需要加任何修饰
  >二进制：数值前面以==0b==开头，b大小写都可
  >八进制：数值前面以==0==开头
  >十六进制：数值前面以==0x==开头，x大小写都可
  >==注意==：书写的时候，虽然加入了进制的标识，但打印在控制台展示的时候都是==十进制==数据

- **进制转换**
  ==任意进制到十进制公式==：系数*基数的权次幂 相加
           系数：每一【位】上的数
           基数：几进制，就是几
           权：从数值的右侧，以0开始，逐个+1增加
  ==十进制到任意进制的转换公式==：除基取余
           使用源数据，不断地==除以基数==（几进制就是除几）得到==余数==，直到商为==0==，再==将余数倒序拼起来==即可
  ==快速进制转换法==：8421码
           8421码又称BCD码，是BCD代码中最常用的一种
           BCD：（Binary-Coded Decimal）二进制码十进制数
           在这种编码方式中，每一位二进制值的1都是代表一个固定数值，把每一位的1代表的十进制数加起来得到的结果就是他所代表的十进制数

- **原码反码补码**
  ==注意==：计算机中的数据，都是以二进制补码的形式在运算，而补码则是通过反码和原码推算出来的
  原码：（可直观的看出数据大小）就是二进制定点表示法，最高位为符号位，0正1负，其余位表示数值的大小
              一个字节等于8个比特位，也就是8个二进制位

  反码：（将原码转换为补码）正数的反码与其原码相同，负数的反码是对其原码逐位取反，但符号位除外
  补码：（数据以该状态进行运算）正数的补码与其原码相同，负数的补码是在其反码的末位加1

  > 正数的原反补都是相同的
  >
  > 负数的【反码】，是根据【原码】取反（0变1，1变0）得到的==（符号位不变）==
  >
  > 负数的【补码】，是根据【反码】的末尾+1得到的

- **位运算**

  - 位运算指的是二进制位的运算，先将十进制数转换成二进制后再进行运算

  - 在二进制位运算中，==1表示true==，==0表示false==
    `&` 位与：遇false则false，遇0则0
    `|` 位或：遇true则true，遇1则1
    `^` 位异或：相同为false，不同为true          (a = a ^ b ^ b)
    `~` 取反：全部取反，0变1，1变0（也包括符号位）

  - 位移运算符：
    `<<` 有符号左移运算，二进制位向左移动，左边符号位丢弃，右边补齐0
           ==运算规律==：向左移动几位，就是乘以2的几次幂

    `>>` 有符号右移运算：二进制位向右移动，使用符号位进行补位
           ==运算规律==：向右移动几位，就是除以2的几次幂

    `>>>` 无符号右移运算符，无论符号位是0还是1，都补0

  - 案例：

    ```java
    // 需求：在不使用第三方变量的情况下，实现两数据交换
    public static void main(String[] args){
        int a = 10;
        int b = 20;
        a = a ^ b;
        b = a ^ b;
        a = a ^ b;
        System.out.println(a);
        System.out.println(b);
    }
    ```

    ```java
    // 需求：实现数组元素的反转（交换数组中元素的值）
    int[] arr = {11, 22, 33, 44, 55, 66, 77};
    for(int start = 0, end = arr.length - 1; start < end; start++, end--){
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
    }
    for(int i = 0 ; i < arr.length; i++){
        System.out.println(arr[i]);
    }
    ```


### 二维数组

- 概述：二维数组也是一种容器，不同于一维数组，该容器存储的都是一维数组容器

- 定义格式
  格式1：`数据类型[][] 变量名;`
  格式2：`数据类型 变量名[];`
  格式3：`数据类型[] 变量名[];`

- 动态初始化：`数据类型[][] 变量名 = new 数据类型[m][n];`
  ==m==表示这个二维数组可以存放多少个一维数组==(行)==
  ==n==表示每一个一维数组，可以存放多少个元素==(列)==

- 拓展：将一个提前创建好的一维数组存储到二维数组中

  ```java
  int[] arr = {11, 22, 33};
  int[][] arr2 = new int[1][3];
  arr2[0] = arr;
  System.out.println(arr2[0][2]);
  ```

- 静态初始化：
  格式：`数据类型[][] 变量名 = new 数据类型[][]{{元素1, 元素2,...}, {元素1, 元素2,...}...};`
  简化格式：`数据类型[][] 变量名 = {{元素1, 元素2,...}, {元素1, 元素2,...}, ...};`

- 二维数组遍历

  ```java
  // 需求：已知一个二维数组arr = {{11, 22, 33}, {33, 44, 55}};  遍历数组，取出所有元素并打印
  int[][] arr = {{11, 22, 33}, {33, 44, 55}};
  for(int i = 0; i < arr.length; i++){
      for(int j = 0; j < arr[i].length; j++){
          System.out.println(arr[i][j]);
      }
  }
  ```

- 案例：

  ```java
  // 需求：二维数组求和
  int sum = 0;
  int[][] arr = {{22, 66, 44}, {77, 33, 88}, {25, 45, 65}, {11, 66, 99}};
  for(int i = 0; i < arr.length; i++){
      for(int j = 0; j < arr[i].length; j++){
          sum += arr[i][j];
      }
  }
  System.out.println(sum);
  ```


## 面向对象基础

### 类和对象

#### 面向对象和面向过程的思想对比

- 面向过程编程(Procedure Oriented Programming)：是一种以**过程**为中心的编程思想，实现功能的每一步，都是==自己实现==的
- 面向对象编程(Object Oriented Programming)：是一种以**对象**为中心的编程思想，通过==指挥对象实现==具体的功能
  对象：指客观存在的事物==（万物皆对象）==

#### 类和对象

- 类是对现实生活中一类具有**共同属性**和**行为**的事物的抽象
  【类】是对事物，也就是对象的一种==描述==，可以将类理解为一张设计图，根据设计图，可以创建出具体存在的事物
- 类的组成
  - 属性：该事物的各种特征
  - 行为：该事物存在的功能（能够做的事情）
- 对象：是能够看得到摸得着的真实存在的实体

> 类是对对象的描述
>
> 对象是类的实体
>
> 一个类可以创建出多个对象

##### 类的定义

- 类的组成：**属性**和**行为**

  - 属性：在代码中通过**成员变量**来体现（类中方法外的变量）
  - 行为：在代码中通过**成员方法**来体现（和前面的方法相比去掉static关键字即可）

- 类的定义步骤

  - 定义类

  - 编写类的成员变量

  - 编写类的成员方法

    ```java
    public class 类名{
        // 成员变量
        变量1的数据类型 变量1;
        String name;		// 未赋值默认null
        变量2的数据类型 变量2;
        int age;			// 未赋值默认0
        ......
        // 成员方法
        方法1;
        public void study(){
            System.out.println("学习");
        }
        方法2;
        ......
    }
    ```

##### 对象的创建和使用

- 创建对象
  格式：`类名 对象名 = new 类名();`
- 使用对象
  使用成员变量：`对象名.变量名`
  使用成员方法：`对象名.方法名();`
  
- 案例

  ```java
  // 需求：定义一个类，然后定义一个手机测试类，在手机测试类中通过对象完成成员变量和成员方法的使用
  public class Phone{
      // 成员变量：品牌、价格、....
      String brand;
      int price;
      // 成员方法：打电话、发短信、....
      public void call(String name){
          System.out.println("给" + name + "打电话");
      }
      public void sendMessage(){
          System.out.println("群发短信");
      }
  }
  ```

### 对象内存图

- 单个对象内存图
  ![](E:\Typora\学习笔记\images\单个对象内存图.png)

- 两个对象内存图
  ![](E:\Typora\学习笔记\images\两个对象内存图.png)

- 两个引用指向同一对象内存图
  - 垃圾回收
    注意：当堆内存中，**对象**或**数组**产生的地址，通过任何方式都==不能被找到==后，就会被判定为内存中的==“垃圾”==
    垃圾会被==Java垃圾回收器==，空闲的时候自动进行清理
- 成员变量和局部变量
  - 成员变量：类中方法外的变量；存放于堆内存；随着对象的存亡而存亡；有默认的初始化值
  - 局部变量：方法中的变量；存放于栈内存；随着方法调用存在，方法调用完毕结束；无默认初始化值，必须先定义、赋值再使用

### 封装

- **private**关键字：权限修饰符，可以用来修饰成员，来提高数据的安全性
  特点：只能在**本类**当中进行访问，外界需要访问可以定义方法来进行**设置值**和**获取值**
  针对private修饰的成员变量，如果需要被其他类引用，提供相应的操作
  		提供`get变量名();`方法，用于获取成员变量的值，方法用**public**修饰
         提供`set变量名();`方法，用于设置成员变量的值，方法用**public**修饰

  ```java
  // 新建Student类
  public class Student{
      private String name;
      private int age;
      
      public void setName(String n){
          name = n;
      }
      public String getName(){
          return name;
      }
      public void setAge(int a){
          age = a;
      }
      public int getAge(){
          return age;
      }
      public void show(){
          System.out.println(name + age);
      }
  }
  ```

- **this**关键字：可以调用本类的成员（变量，方法），解决局部变量和成员变量重名问题
  局部变量和成员变量如果重名，Java使用的是就近原则
  `this`代表所在类的对象引用，方法被哪个对象调用，this就代表哪个对象

  ```java
  public class Student{
      private int age;
      public void method(int age){
          this.age = age;			// 添加this关键字，使前一个age成为成员变量，再将局部变量age赋值过去
      }
  }
  ```

  - this内存原理

- **封装**

  - 面向对象三大特征之一（**封装**、**继承**、**多态**）
  - 隐藏实现细节，仅对外暴露公共的访问方式（类似于插线板）
  - 常见体现：
    - 将**代码**抽取到**方法**中，是对**代码**的一种封装；将**属性**抽取到**类**中，是对**数据**的一种封装
    - 私有的成员变量，提供setXxx和getXxx方法
  - 好处
    - 提高了代码的安全性
    - 提高了代码的复用性

### 构造方法

- 构建、创造对象的时候，所调用的方法

- 格式：

  1. 方法名与类名相同，大小写也要一致
  2. 没有返回值类型，连void也没有
  3. 没有具体的返回值（不能由return带回结果数据）

  ```java
  public class Student{
      public Student(){
          System.out.println("这是Student类的构造方法");
      }
  }
  ```

- 执行时机：

  1. 创建对象的时候调用，每创建一次对象，就会执行一次构造方法
  2. 不能手动调用构造方法

- 作用：用于**给对象**的数据**（属性）**进行==初始化==

  ```java
  class Student{
      private int age;
      public Student(int age){
          this.age = age;
      }
  }
  ```

- 注意事项

  构造方法的创建：
  	如果没有定义构造方法，系统将给出一个**默认**的**无参数的构造方法**
  	如果定义了构造方法，系统将不再提供默认的构造方法

- 标准类的代码编写和使用

  ```java
  /*
  	JavaBean类：封装数据的类
  */
  public class Student{
      // 私有变量
      private String name;
      private int age;
      
      // 无参数构造方法
      public Student(){}
      //有参数构造方法
      public Student(String name, int age){
          this.name = name;
          this.age = age;
      }
      
      //set/get方法
      public void setName(String name){
          this.name = name;
      }
      
      public String getName(){
          return name;
      }
      
      public void setAge(int age){
          this.age = age;
      }
      
      public String getAge(){
          return age;
      }
  }
  ```

## API基础

- API(**A**pplication **P**rogramming **I**nterface):应用程序编程接口
  编写程序去控制踢足球，程序需要向机器人发出向前跑、向后跑、射门、抢球等各种命令。机器人厂商一定会提供一些用于控制机器人的接口类，这些类中定义好了操作机器人各种动作的方法。其实，这些接口类就是机器人厂商提供给应用程序编程的接口，大家把这些类称为API。

- 键盘录入字符串

  ```java
  Scanner sc = new Scanner();
  System.out.print("请输入内容：");
  String s = sc.nextLine(System.in);		遇到回车、换行结束
  //String s = sc.next(System.in);		遇到空格、tab就停止
  System.out.println(s);
  // 在键盘录入接收数据的时候，如果是字符串和整数一起接收，建议使用next方法接收字符串
  ```

### String类

- 概述：String类在**java.lang**包下，使用时不需要导包。
  			String类代表字符串，Java程序中的所有字符串字面值（如："abc"）都作为此类的方法实现
    			字符串是常量，它们的值在创建后不能更改

- 常见构造方法
  `public String()`             创建一个空白字符串对象，不含有任何内容
  `public String(char[] chs)`          根据字符数组的内容，来创建字符串
  `public String(String original)`         根据传入的字符串内容，来创建字符串对象
  `String s = "abc";`                    直接赋值的方式创建字符串对象，内容就是abc

  > String 这个类比较特殊，打印其对象名的时候，不会出现内存地址，而是该对象所记录的真实内容

- 创建字符串对象的区别对比
  以""方式给出的字符串，只要字符序列相同（顺序和大小写），无论在程序代码中出现几次，JVM都只会建立一个String对象，并在字符串常量池中维护

  > 字符串常量池：当使用==双引号创建字符串对象的时候==，系统会==检查该字符串是否在字符串常量池中存在==。若不存在，则创建；存在则不会重新创建，直接使用
  >
  > 注意：字符串常量池从JDK7开始，从方法区挪到了堆内存
  > 扩展：`==`在比较基本数据类型时比较值，在比较引用数据类型时比较地址是否相同

  通过new创建的字符串对象，每一次new都会申请一个内存空间，虽然内容相同，但是地址值不同

- 特点：
  Java程序中所有双引号字符，都是String类的对象
  字符串不可变，它们的值在创建后不能被更改
  虽然String的值是不可变的，但是他们可以被共享

> 当字符串之间使用 + 拼接的时候，系统底层会自动创建一个StringBuilder对象
> 然后再调用其append方法完成拼接
> 拼接后，再调用toString方法转换为String类型

- 字符串比较
  字符串是对象，他比较内容是否相同，是通过一个方法来实现的，这个方法叫：`equals()`

  - public boolean **equals(Object anObject)**:将此字符串与指定对象进行比较。由于我们比较的是字符串对象，所以参数之间传递一个字符串

    ```java
    String s1 = "abc";
    String s2 = "ABC";
    s1.equals(s2);		//false
    //equalsIgnoreCase()方法比较字符串不区分大小写
    s1.equalsIgnoreCase(s2);		//true	
    ```

- 案例

  ```java
  // 需求：已知用户名和密码，请用程序实现模拟用户登录，总共给三次机会，登录之后，给出相应的提示
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          String userName = "abcde";
          String passWord = "abc666";
          int count = 0;
          Scanner sc = new Scanner(System.in);
          for(int i = 0; i < 3; i++){
              System.out.print("请输入用户名：");
              String user = sc.nextLine();
              System.out.print("请输入密码：");
              String pass = sc.nextLine();
              if(userName.equals(user) && passWord.equals(pass)){
                  System.out.println("恭喜您，登录成功！");
                  break;
              }else{
                  System.out.println("账号或密码错误，请重试");
                  count++;
              }
          }
          if(count >= 3) System.out.println("登录失败次数过多，请稍后重试");
      }
  }
  ```

  ```java
  // 需求：键盘录入一个字符串，使用程序实现在控制台遍历该字符串，将字符串拆分为字符数组
  // public char charAt(int index):返回指定索引处的char值，字符串的索引也是从0开始的
  // public int length():返回此字符串的长度
  // public char[] toCharArray():将当前字符串拆分为字符数组并返回
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入字符串：");
          String s = sc.nextLine();
          /*
          for(int i = 0; i < s.length(); i++){
              System.out.print(s.charAt(i) + " ");
          }
          */
          char[] chars = s.toCharArray();
          for(int i = 0; i < chars.length; i++){
              System.out.print(chars[i] + " ");
          }
      }
  }
  ```

  ```java
  //需求： 键盘录入一个字符串，统计该字符串中大写字母字符，小写字母字符，数字字符出现的次数（不考虑其他字符）
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入字符串：");
          String s = sc.nextLine();
          char[] chars = s.toCharArray();
          int num = 0;
          int english = 0;
          int English = 0;
          for(int i = 0; i < chars.length; i++){
              if(chars[i] >= '0' && chars[i] <= '9') num++;
              else if(chars[i] >= 'a' && chars[i] <= 'z') english++;
              else if(chars[i] >= 'A' && chars[i] <= 'Z') English++;
          }
          System.out.println("数字：" + num + " 小写字母：" + english + " 大写字母:" + English);
      }
  }
  ```

  ```java
  // 需求：以字符串的形式从键盘接收一个手机号，将中间四位号码屏蔽
  // 最终效果：183****4828
  /*
  	截取字符串：
  		String substring(int beginIndex):
  			从传入的索引位置处，向后截取，一直截取到末尾，得到新的字符串并返回
          String substring(int beginIndex, int endIndex):
          	从beginIndex索引位置开始截取，截取到endIndex索引位置，得到新的字符串并返回（含头不含尾）
  */
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入手机号：");
          String s = sc.nextLine();
          String begin = s.substring(0, 3);
          String end = s.substring(7, 11);
          System.out.println("最终手机号为：" + begin + "****" + end);
      }
  }
  ```

  ```java
  // 需求：键盘录入一个字符串，如果字符串中包含（TMD），则使用***替换
  /*
  	String replace(CharSequence target, CharSequence replacement)
  		将当前字符串中的target(被替换的旧值)内容，使用replacement(替换的新值)进行替换
  		返回新的字符串
  */
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入内容：");
          String s = sc.nextLine();
          String result = s.replace("TMD", "***");
          System.out.println("您输入的内容为：" + result);
      }
  }
  ```

  ```java
  // 需求：以字符串的形式从键盘录入学生信息，例如："张三,23"从该字符串中切割出有效数据，封装为Student学生对象
  // String[] split(String regex):根据传入的字符作为规则进行切割，将切割后的内容存入字符串数组中，并将字符串返回(数组)
  11
  11
  // 新建一个Student类
  public class Student{
      private String name;
      private String age;
      public Student(){}
      public Student(String name, String age){
          this.name = name;
          this.age = age;
      }
      public String getName(){
          return name;
      }
      public void setName(String name){
          this.name = name;
      }
      public String getAge(){
          return age;
      }
      public void setAge(String age){
          this.age = age;
      }
  }
  
  //---------------------------下面为一个新的class文件----------------------------------------------
  
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入您的信息：");
          String stuInfo = sc.nextLine();
          String[] sArr = stuInfo.split(",");
          Student stu = new Student(sArr[0], sArr[1]);
          System.out.println("姓名：" + stu.getName() + " 年龄：" + stu.get)
      }
  }
  ```


### StringBuilder

- 概述：StringBuilder 是一个可变的字符串类，我们可以把它看成是一个容器

- 作用：提高字符串的操作效率

- 构造方法：
  `public StringBuilder()`        创建一个空白可变字符串对象，不含有任何内容
  `public StringBuilder(String str)`         根据字符串的内容，来创建可变字符串对象

- 常用方法：
  `public StringBuilder append(任意类型)`            添加数据，并返回对象本身
  `public StringBuilder reverse()`                返回相反的字符序列
  `public int length()`                 返回长度（字符出现的个数）
  `public String toString()`           通过toString()就可以实现把StringBuilder转换为String

  | 方法名                                | 说明                                                |
  | ------------------------------------- | --------------------------------------------------- |
  | public StringBuilder append(任意类型) | 添加数据，并返回对象本身                            |
  | public StringBuilder reverse()        | 返回相反的字符序列                                  |
  | public int length()                   | 返回长度（字符出现的个数）                          |
  | public String toString()              | 通过toString()就可以实现把StringBuilder转换为String |
  
  
  
  ```java
  StringBuilder sb = new StringBuilder();
  //链式编程：如果一个方法返回的是对象类型，对象就可以继续向下调用方法
  sb.append("red").append("blue").append("green");
  ```
  
- StringBuilder 提高效率原理：
  当String类型字符串以 + 拼接时，系统默认在堆内存中new一个StringBuilder类型对象，通过append()方法完成拼接，再通过toString()将StringBuilder类型转换为String类型。
  而使用StringBuilder则可以省去不必要的步骤

- 案例

  ```java
  // 需求：键盘接收一个字符串，程序判断出该字符串是否是对称字符串，并在控制台打印是或不是
  // 对称字符串：123321、111			非对称字符串：123123
  import java.util.Scanner;
  public class Test{
      public static void main(String[] args){
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入内容：");
          String s = sc.nextLine();
          StringBuilder ss = new StringBuilder(s);
          String sss = ss.reverse().toString();
          if(s.equals(sss)){
              System.out.println("是");
          }else{
              System.out.println("不是");
          }
      }
  }
  ```

  ```java
  // 需求：定义一个方法，把int数组中的数据按照指定的格式拼接成一个字符串返回，调用该方法，并在控制台输出结果。
  // 例如：数组为：int[] arr = {1, 2, 3};	执行方法后的输出结果为：[1,2,3]
  public static void main(String[] args){
      int[] arr = {1, 2, 3};
      String s = arrayToString(arr);
      System.out.println(s);
  }
  // 定义一个方法，返回值类型 String ，参数列表int[] arr
  public static String arrayToString(int[] arr){
      StringBuilder sb = new StringBuilder("【");
      for(int i = 0; i < arr.length; i++){
          if(i == arr.length - 1){
              sb.append(arr[i]).append("】");
          }else{
              sb.append(arr[i]).append(",");
          }
      }
      return sb.toString();
  }
  ```

## 集合基础

-  对象数组

  ```java
  // 需求：将(张三,23)(李四,24)(王五,25)封装为3个学生对象并存入数组，随后遍历数组，将学生信息输出
  // 新建一个Student类
  public class Student{
      private String name;
      private String age;
      public Student(){}
      public Student(String name, String age){
          this.name = name;
          this.age = age;
      }
      public String getName(){
          return name;
      }
      public void setName(String name){
          this.name = name;
      }
      public String getAge(){
          return age;
      }
      public void setAge(String age){
          this.age = age;
      }
  }
  
  //---------------------------下面为一个新的class文件----------------------------------------------
  
  public class Test{
      public static void main(String[] args){
          Student[] arr = new Student[3];
          Student stu1 = new Student("张三","23");
          Student stu2 = new Student("李四","24");
          Student stu3 = new Student("王五","25");
          arr[0] = stu1;
          arr[1] = stu2;
          arr[2] = stu3;
          for(int i = 0; i < arr.length; i++){
              System.out.println("姓名：" + arr[i].getName() + " 年龄：" + arr[i].getAge());
          }
      }
  }
  ```

### 集合和数组的特点对比

- 集合类的特点：提供一种存储空间可变的存储类型，存储的数据容量可以发生改变
- 集合和数组的区别：
  **共同点**：都是存储数据的==容器==
  **不同点**：数组的容量是==固定==的，集合的容量是==可变==的
  **如果存储的数据，长度经常发生改变，推荐使用集合**

### ArrayList集合

- 构造方法：`ArrayList()`  构造一个初始容量为10的空列表

- 成员方法：
  `boolean add(E e)`  将指定的元素添加到此列表的尾部
  `void add(int index, E element)`   将指定的元素插入此列表中的指定位置

  > 如果没有进行数据类型的限制，可以添加任何数据类型的数据
  >
  > 如果要进行限制，格式为：`ArrayList<数据类型> list = new ArrayList<数据类型>();`
  >
  > JDK7版本以后，可写为：`ArrayList<数据类型> list = new ArrayList<>();`
  >
  > <E>：是一种特殊的数据类型，泛型。<>里面只能写引用数据类型，int、double等基本数据类型不行

  `public boolen remove(Object)`      删除指定的元素，返回是否删除成功,只能删除第一个匹配到的元素
  `public E remove(int index)`		删除指定索引处的元素，返回被删除的元素
  `public E set(int index, E element)`		修改指定索引处的元素，返回被修改的元素
  `public E get(int index)`			返回指定索引处的元素
  `public int size()`			返回集合中的元素的个数

### 案例

```java
// 需求：创建一个存储字符串的集合，存储3个字符串元素，使用程序实现在控制台遍历该集合

import java.util.ArrayList;
public class Test{
    public static void main(String[] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("aaa");
        list.add("bbb");
        list.add("ccc");
        for(int i = 0; i < list.size(); i++){
            System.out.println(list.get(i));
        }
    }
}
```

```java
// 需求：创建一个存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合

// 新建一个Student类
public class Student{
    // 成员变量
    private String name;
    private int age;
    // 构造方法
    public Student(){}
    public Student(String name, int age){
        this.name = name;
        this.age = age;
    }
    //成员方法
    public void setName(String name){
        this.name = name;
    }
    public String getName(){
        return name;
    }
    public void setAge(int age){
        this.age = age;
    }
    public int getAge(){
        return age;
    }
}

//---------------------------下面为一个新的class文件----------------------------------------------

import java.util.ArrayList;
public class Test{
    public static void main(String[] args){
        ArrayList<Student> list = new ArrayList<>();
        Student stu1 = new Student("张三",23);
        Student stu2 = new Student("李四",24);
        Student stu3 = new Student("王五",25);
        list.add(stu1);
        list.add(stu2);
        list.add(stu3);
        for(int i = 0; i < list.size(); i++){
            System.out.println("姓名：" + list.get(i).getName() + " 年龄：" + list(i).getAge());
        }
    }
}
```

```java
// 需求：创建一个存储String的集合，内部存储（test,张三,李四,test,test）字符串，删除所有的test字符串，将删除后的集合元素打印到控制台

import java.util.ArrayList;
public class Test{
    public static void main(String[] args){
        ArrayList list = new ArrayList();
        list.add("test");
        list.add("张三");
        list.add("李四");
        list.add("test");
        list.add("test");
        for(int i = 0; i < list.size(); i++){
            if("test".equals(list.get(i))){		// 变量和常量调用方法，尽量常量去调用，减少不必要的错误
                list.remove(i);
                i--;
            }
        }
        System.out.println(list);
    }
}
```

```java
// 需求：定义一个方法，方法接收一个集合对象（泛型为Student），方法内部将年龄低于18的学生对象找出并存入新集合对象，方法返回新集合
// 新建student类步骤省略

import java.util.ArrayList;
public static void main(String[] args){
    Student stu1 = new Student("张三",23);
    Student stu2 = new Student("李四",16);
    Student stu3 = new Student("王五",22);
    Student stu4 = new Student("赵六",13);
    Student stu5 = new Student("马七",18);
    ArrayList<Student> list = new ArrayList<>();
    list.add(stu1);
    list.add(stu2);
    list.add(stu3);
    list.add(stu4);
    list.add(stu5);
    ArrayList<Student> newList = getList(list);
    for(int i = 0; i < newList.size(); i++){
        System.out.println("姓名：" + newList.get(i).getName() + " 年龄：" + newList.get(i).getAge());
    }
}
public static ArrayList<Student> getList(ArrayList<Student> list){
    ArrayList<Student> newList = new ArrayList<>();
    for(int i = 0; i < list.size(); i++){
        if(list.get(i).getAge() < 18){
            newList.add(list.get(i));
        }
    }
    return newList;
}
```

### 学生管理系统

- 实现思路

  1. 定义学生类

     ```java
     public class Student{
         // 成员变量
         private int sid;				//学号
         private String name;			//姓名
         private int age;				//年龄
         private String birthday;		//生日
         // 构造方法
         public Student(){}
         public Student(int sid, String name, int age, String birthday){
             this.sid = sid;
             this.name = name;
             this.age = age;
             this.birthday = birthday;
         }
        // 成员方法
         public void setSid(int sid){
             this.sid = sid;
         }
         public int getSid(){
             return sid;
         }
         public void setName(String name){
             this.name = name;
         }
         public String getName(){
             return name;
         }
         public void setAge(int age){
             this.age = age;
         }
         public int getAge(){
             return age;
         }
         public void setBirthday(String birthday){
             this.birthday = birthday;
         }
         public String getBirthday(){
             return birthday;
         }
     }
     ```

  2. 主界面代码编写

     ```java
     import java.util.Scanner;
     import java.util.ArrayList;
     
     public class studentManager {
         public static void main(String[] args) {
             Scanner sc = new Scanner(System.in);
             ArrayList<Student> list = new ArrayList<>();	// 创建一个容器
             // 搭建主界面菜单
             lo:			//添加一个标号，配合break完成退出操作
             while (true) {
                 System.out.println("-------欢迎来到学生信息管理系统-------");
                 System.out.println("1.添加学生");
                 System.out.println("2.删除学生");
                 System.out.println("3.修改学生");
                 System.out.println("4.查看学生");
                 System.out.println("5.退出");
                 System.out.println("---------------------------------");
                 System.out.print("请输入您的选择：");
                 int choice = sc.nextInt();
                 switch (choice) {
                     case 1:
                         addStudent(list);
                         break;
                     case 2:
                         delStudent(list);
                         break;
                     case 3:
                         System.out.println("修改");
                         break;
                     case 4:
                         queryStudent(list);
                         break;
                     case 5:
                         System.out.println("您已退出，感谢您的使用");
                         break lo;
                     default:
                         System.out.println("您的输入有误，请重新输入");
                         break;
                 }
             }
         }
     }
     ```

  3. 添加学生的代码编写

     ```java
     // addStudent
     public static void addStudent(ArrayList<Student> list){
         Scanner sc = new Scanner(System.in);
         int sid;		// 写在while外面，方便整个addSt
         while(true){
             System.out.print("请输入学号：");
         	sid = sc.nextInt();
             int index = getIndex(list, sid);
             if(index == -1){
                 break;
             }else{
                 System.out.println("该学号已存在，请重新输入");
             }
         }
         System.out.print("请输入姓名：");
         String name = sc.next();
         System.out.print("请输入年龄：");
         int age = sc.nextInt();
         System.out.print("请输入生日：");
         String birthday = sc.next();
         Student stu = new Student(sid, name, age, birthday);
         list.add(stu);
         System.out.println("恭喜您，添加成功！");
     }
     ```

  4. 查看学生的代码编写

     ```java
     // queryStudent
     public static void queryStudent(ArrayList<Student> list){
         if(list.size() == 0){
             System.out.println("当前无数据，请添加数据后重试");
         }
         else{
             System.out.println("学号\t\t\t姓名\t\t年龄\t\t生日");
             for(int i = 0; i < list.size(); i++){
                 Student stu = list.get(i);
                 System.out.println(stu.getSid() + "\t\t\t" + stu.getName() + "\t\t" + stu.getAge() + "\t\t" + stu.getBirthday());
             }
         }
     }
     ```

  5. 删除/修改学生学号不存在问题

     ```java
     // 定义一个方法(getIndex)，用于从集合中查找【学号】在【集合】中出现的索引位置
     public static int getIndex(ArrayList<Student> list, int sid){
         int index = -1;		//假设传入的学号不存在
         for(int i = 0; i < list.size(); i++){
             Student stu = list.get(i);
             int id = stu.getSid();
             if(id == sid){
                 index = i;
             }
         }
         return index;
     }
     ```

  6. 删除学生的代码编写

     ```java
     // delStudent
     public static void delStudent(ArrayList<Student> list){
         Scanner sc = new Scanner(System.in);
         System.out.print("请输入您要删除的学生学号：");
         int delSid = sc.nextInt();
         int index = getIndex(list, delSid);
         if(index == -1){
             System.out.println("查无信息，请重新输入");
         }else{
             list.remove(index);
             System.out.println("恭喜您，删除成功！");
         }
     }
     ```

  7. 修改学生的代码编写

     ```java
     // updateStudent
     public static void updateStudent(ArrayList<Student> list){
         Scanner sc = new Scanner(System.in);
         System.out.print("请输入您要修改的学生学号：");
         int updateSid = sc.nextInt();
         int index = getIndex(list, updateSid);
         if(index == -1){
             System.out.println("查无信息，请重新输入");
         }else{
             System.out.print("请输入新的学生姓名：");
             String name = sc.next();
             System.out.print("请输入新的学生年龄：");
             int age = sc.nextInt();
             System.out.print("请输入新的学生生日：");
             String birthday = sc.next();
             Student stu = new Student(updateSid, name, age, birthday);
             list.set(index, stu);
             System.out.println("恭喜您，修改成功！");
         }
     }
     ```

## Git

### 概述及安装

- 版本控制：无论是代码编写，还是文档编写，我们都会遇到对文档内容反复修改的情况
- Git和SVN的对比
  - SVN是**集中式**版本控制系统，版本库是集中放在**中央服务器**的，而开发人员工作的时候，用的都是自己的电脑，所以首先要从中央服务器下载最新的版本，然后开发，开发完后，需要把自己开发的代码提交到中央服务器
  - Git是在2005年，Liunx创建者为了帮助全球的开发者，维护Linux系统内核的开发，而开发了自己的开源分布式版本控制工具，分为两种类型的仓库，**本地仓库**和**远程仓库**
- Git下载和安装
  官网下载地址：<https://git-scm.com/downloads>
  Git GUI : Git提供的图形界面工具
  Git Bash：Git提供的命令行工具
  运行Git命令客户端，使用git --version命令，可以查看git版本
- TortoiseGit安装

### 基本操作

#### 本地仓库

- 工作目录：Working Tree		----代码存放的位置
- 暂存区(Index)：代码提交到仓库之前的==临时存储空间==
- 本地历史仓库(Repository)：存放不同版本的代码，例如：（完成了项目10%的代码、完成了项目20%的代码）

> 工作目录---->暂存区---->本地历史仓库

#### Git常用命令

- git init：初始化，创建git仓库
- git status：查看git状态（文件是否进行了添加、提交操作）
- git add 文件名：添加，将指定文件添加到暂存区
- git commit -m '描述信息'：提交，将暂存区文件提交到历史仓库
- git log：查看日志（git提交的历史日志）
- 基本操作流程
  1. 创建工作目录，初始化本地git仓库
  2. 新建一个test.txt文件（暂不执行添加操作）
  3. 使用status命令，查看状态
  4. 使用add命令添加，并查看状态
  5. 使用commit命令，提交到本地历史仓库
  6. 使用log命令，查看日志
  7. 修改test.txt文件
  8. 添加并提交，查看日志

#### TortoiseGit操作

可视化操作

#### Git版本管理

- 准备工作：
  1. 查看log日志
     	git reflog：可以查看所有分支的所有操作记录（包括已经被删除的commit记录的操作）
  2. 增加一次新的修改记录
- 主要指令
  git reflog
  git reset --hard 版本唯一索引值：将代码切换到指定版本

#### 分支管理

- 分支：由每次提交的代码，串成的一条时间线

- 特点：两条时间线，并行工作，互不打扰，==多条时间线可以合并==
- 使用场景：
  1. 周期较长的模块开发
  2. 尝试性的模块开发
- 使用分支意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线 

- 工作流程

  1. 创建新分支：`git branch 分支名`

  2. 切换分支: `git checkout 分支名`

     > 查看文件命令：`ls`				查看分支列表命令：`git branch`
     >
     > 不同分支之间是平行关系，在工作时不会相互影响

  3. 合并分支:：`git merge 分支名`

  4. 删除分支：`git branch -d 分支名`

#### 远程仓库

- 工作流程
  推送(push)：推送本地仓库内容到远程仓库
  克隆(clone)：将远程仓库中的内容复制到本地仓库
  拉取(pull)：更新远程仓库中新的内容到本地仓库（和克隆有区别）

#### 常见远程仓库平台

- GitHub：
  域名：<https://github.com>
  介绍：GitHub是全球最大的开源项目托管平台，俗称大型程序员社区化交友网站
  			各类好玩有趣的开源项目，只有想不到，没有找不到

- 码云：
  域名：<https://gitee.com>
  介绍：码云是全国最大的开源项目托管平台，良心平台，速度快，提供免费私有库

- 远程仓库平台操作
  情况：
         **1.先有本地仓库，远程仓库为空**
         **2.先有远程仓库，本地仓库为空**

- 情况1
  步骤：

  1. 创建远程仓库

  2. 将项目从本地仓库，推送到远程仓库
     **注意：**在推送代码之前，需要先配置SSH公钥

     > 生成SSH公钥步骤：
     >
     > 1. 设置Git账户
     >    查看git账户：`git config user.name`
     >    查看git邮箱：`git config user.email`
     >    设置全局账户名和邮箱：`git config --global user.name "账户名"`
     >    											`git config --global user.email "邮箱"`
     > 2. 生成SSH公钥
     >    查看是否生成过SSH公钥：`cd ~/.ssh`
     >    生成SSH：`ssh-keygen -t rsa -C "邮箱"`                这里需要敲击三次回车
     >    查看SSH：`cat ~/.ssh/id_rsa.pub`
     > 3. 设置账户公钥（在远程仓库平台设置）
     > 4. 公钥测试：`ssh -T git@gitee.com`

  3. 推送到远程平台
     步骤：
     1. 为远程仓库的URL（网址），自定义仓库名称：`git remote add 远程名称 远程仓库URL`
     2. 推送：`git push -u 仓库名称 分支名`

- 情况2：
  步骤：

  1. 将远程仓库的代码，克隆到本地仓库：`git clone 仓库地址`
  2. 创建新文件，添加并提交到本地仓库
  3. 推送至远程仓库
  4. 项目拉取更新：`git pull 远程仓库名 分支名`

- 代码冲突

  ![](E:\Typora\学习笔记\images\代码冲突.png)

  ​				**<<<<<<<和>>>>>>>>>中间的内容，就是冲突部分**

  1. 修改冲突行，保存，即可解决冲突
  2. 重新add冲突文件并commit到本地仓库，重新push到远程

#### IDEA集成Git

- IDEA中配置Git
  1. File ---- Settings
  2. Version Control ---- Git ---- 指定git.exe存放目录
  3. 点击Test测试

- 版本切换
  ==Reset Current Branch to Here...==             会抛弃原来的提交记录
  ==Revert Commit==             需要进行版本冲突处理，历史记录还保留提交记录

- 远程仓库操作
  - 本地推送到远程
  - 远程克隆到本地

## 面向对象进阶

### 分类和static

#### 分类思想

- 分类思想：分工协作，专人干专事
- 黑马信息管理系统分类
  - Student类：标准学生类，封装键盘录入的学生信息（id,name,age,birthday）
  - StudentDao类：Dao:(Data Access Object缩写)用于访问存储数据的数组或集合
  - StudentService类：用来进行业务逻辑的处理（例如：判读录入的id是否存在）
  - StudentController类：和用户打交道（接收用户需求，采集用户信息，打印数据到控制台）

#### 分包思想

- 分包思想：如果将所有的**类文件都放在同一个包下，不利于管理和后期维护**
  					所以，对于**不同功能的类文件**，可以**放在不同的包下进行管理**

- 包：本质上就是文件夹

- 创建包：（单级包、多级包）
  多级包之间使用"."进行分割
  多级包的定义规范：公司的网站地址翻转（去掉www）
  比如：黑马程序员的网站为www.itheima.com
  后期所定义的包结构就是:com.itheima.其他的包名。

- 包的命名规则：英文字母都是小写

- 包的定义

  - 使用`package`关键字定义包
  - 格式：`package 包名;`如果是多级包，中间用"."进行分割

- 包的注意事项

  - package语句必须是程序的第一条可执行代码
  - package语句在一个Java文件中只能有一个
  - 如果没有package，默认表示无包名

- 类与类之间的访问

  - 同一个包下的访问
    不需要导包，直接使用即可
  - 不同包下的访问
    1. import 导包后访问
    2. 通过全类名（包名+类名）访问
       应用场景：多个包下，出现了相同的类名，就可以使用这种方式进行区分

- 注意事项

  import、package、class三个关键字的摆放位置存在顺序关系

  - package必须是程序的第一条可执行代码
  - import需要写在package下面
  - class需要在import下面

#### 黑马信息管理系统

- 需求说明
  - 添加学生：键盘录入学生信息（id,name,age,birthday）
    					使用**数组存储学生信息**，要求学生**id不能重复**
  - 删除学生：键盘录入学生的id值，将该学生从数组中移除，**如果录入的id不存在，需要重新录入**
  - 修改学生：键盘录入要修改的学生的id值和修改后的学生信息
    					将数组中该学生的信息修改，**如果录入的id在数组中不存在，需要重新录入**
  - 查询学生：将数组中存储的所有学生的信息输出到控制台
  - **使用分类思想、分包思想完成**

- 环境搭建

  - 创建模块：itheima-edu-info-manager

  - 创建包、创建类

    |                   包                    |        存储的类        |                   作用                   |
    | :-------------------------------------: | :--------------------: | :--------------------------------------: |
    |   com.itheima.edu.info.manager.domain   |      Student.java      |               封装学生信息               |
    |    com.itheima.edu.info.manager.dao     |    StudentDao.java     | 访问存储数据的数组，进行增删改查（库管） |
    |  com.itheima.edu.info.manager.service   |  StudentService.java   |         业务的逻辑处理（业务员）         |
    | com.itheima.edu.info.manager.controller | StudentController.java |         和用户打交道（客服接待）         |
    |   com.itheima.edu.info.manager.entry    | InfoManagerEntry.java  |      程序的入口类，提供一个main方法      |

- 思路分析：

  - 添加学生
    StudentController(客服接待):

     	1. 方法中接收用户输入的信息
     	2. 将学生信息封装为学生对象并传递给StudentService
     	3. 接收方法的boolean类型返回值，根据结果在控制台打印添加成功/添加失败

    StudentService(业务员)：

    1. 将接收到的学生对象，传递给StudentDao
    2. 接收方法的boolean返回值，将结果返还给StudentController

    StudentDao(库管)：

    1. 创建Student学生数组长度为5
    2. 将接收到的学生对象添加到数组中
    3. 返回是否添加成功的boolean类型值

- static关键字

  **static**关键字是静态的意思，修饰符，可以修饰成员变量、成员方法
  		 被static修饰的成员变量，一般叫做静态变量
  	 	被static修饰的成员方法，一般叫做静态方法

  - 特点
    被类所有的对象共享，是我们判断是否使用静态关键字的条件
    随着类的加载而加载，优先于对象存在，对象需要类被加载后，才能创建
    可以通过类名调用，也可以通过对象名调用，==推荐使用类名调用==
  - 注意
    静态方法中，只能访问静态成员（成员变量、成员方法）
    静态方法中，没有this关键字

### 老师管理系统

### 继承

#### 概述

- 继承：让**类于类之间产生关系**（子父类关系），==子类==可以==直接使用==父类中==非私有的成员==
- 格式：`public class 子类名 extends 父类名{}`
- 范例：`public class Zi extends Fu{}`
- Fu:是父类，也被称为基类、超类
- Zi：是子类，也被称为派生类

#### 优劣

- 优点

  - 提高了代码的复用性
  - 提高了代码的维护性
  - 让类与类之间产生了关系，是多态的前提

- 弊端

  - 继承是侵入性的

  - 降低了代码的灵活性
    继承关系，导致子类==必须拥有==父类非私有属性和方法，让子类自由的世界中多了些约束

  - 增强了代码的耦合性

    > 耦合性：代码与代码之间存在的关联都可以称之为“耦合”。

- 应用场景
  - 当类与类之间，存在相同（共性）的内容，并且产生了is a的关系，就可以考虑使用继承，来优化代码
- Java继承的特点
  - Java只支持**单继承**，不支持**多继承**，但支持**多层继承**

#### 成员变量

- 访问特点
  - 子类局部范围找
  - 子类成员范围找
  - 父类成员范围找

- 注意：如果子父类中，出现了==重名的成员变量==，通过==就近原则==，会==优先使用子类==的
  			如果一定要使用父类的，可以通过`super`关键字进行区分
- super关键字
  - `super`和`this`关键字的用法相似
  - this：代表本类对象的引用
  - super：代表父类存储空间的标识（可以理解为父类对象引用）

#### 成员方法

- 访问特点
  - 子类成员范围找
  - 父类成员范围找

#### 方法重写

- 概述：在继承体系中，子类出现了和父类中一模一样的方法声明

- 应用场景

  - 当子类需要父类的功能，而功能主体子类有自己特有内容，可以重写父类中的方法，这样，既沿袭了父类的功能，又定义了子类特有的内容

- 区别

  > 方法重写：在继承体系中，子类出现了和父类一模一样的方法声明（方法名，参数列表，返回值类型）
  >
  > 方法重载：在同一个类中，方法名相同，参数列表不同，与返回值无关
  >
  > 

- 注意事项

  - 父类中私有方法不能被重写

  - 父类==静态方法==，子类必须==通过静态方法==进行==重写==，父类==非静态方法==，子类也==必须通过非静态方法==进行==重写==

    > 静态方法不能被重写！如果子类中，也存在一个方法声明一模一样的方法，可以理解为，子类将父类中同名的方法，隐藏了起来，并非是方法重写！

  - 子类重写父类方法时，访问权限必须大于等于父类

#### 权限修饰符

|   修饰符    | 同一个类中 | 同一个包中子类无关类 | 不同包的子类 | 不同包的无关类 |
| :---------: | :--------: | :------------------: | :----------: | :------------: |
| **private** |     √      |                      |              |                |
|    默认     |     √      |          √           |              |                |
|  protected  |     √      |          √           |      √       |                |
| **public**  |     √      |          √           |      √       |       √        |

#### 构造方法

- 子类中所有的构造方法默认都会访问父类中无参的构造方法

  > 子类在初始化的时候，有可能会使用到父类中的数据，如果父类没有完成初始化，子类将无法使用父类的数据(子类在初始化前，一定要先完成父类的初始化)

- 构造方法的第一条语句默认都是:`super();`
- 注意：如果我们编写的类，没有手动指定父类，系统也会自动继承Object（Java继承体系中的最顶层父类）
- 访问特点
  - 如果父类中没有空参构造方法，只有带参构造方法，会出现错误
    - 子类通过super，手动调用父类的带参构造方法
  - **注意：**this()和super()必须放在构造方法的第一行有效语句，并且二者不能共存

### 抽象类

#### 入门

- 抽象方法：将**共性的**行为（方法），抽取到**父类**之后，发现该方法的==实现逻辑==**无法在父类中给出具体明确**，该方法就可以定义为抽象方法。
- 抽象类：如果一个**类**中存在**抽象方法**，那么该类就必须声明为**抽象类**。
- 定义格式
  - 抽象方法：`public abstract 返回值类型 方法名(参数列表);`
  - 抽象类：`public abstract class 类名{}`

#### 注意事项

- 抽象类不能实例化（创建对象）
- 抽象类中有构造方法
- 抽象类的子类
  - 要么重写父类中所有的抽象方法
  - 要么将自己也变成一个抽象类（了解）
- 抽象类中的方法
  - 抽象类中可以没有抽象方法，但是有抽象方法的类一定是抽象类

#### 模板设计模式

- 设计模式（Design pattern）是一套被反复使用、多数人知晓的、经过分类编目的、代码设计经验的总结。

  使用设计模式是为了可重用代码、让代码更容易被他人理解、保证代码可靠性、程序的重用性。
  通俗来说就是==写代码的风格==

- 模板设计模式：把抽象整体就可以看做成一个模板，模板中不能决定的东西定义成抽象方法
  							让使用模板的类（继承抽象类的类）去重写抽象方法实现需求

- 优势：模板已经定义了通用结构，使用者只需要关心自己需要实现的功能即可

#### final关键字

- **final**修饰的特点

  - 修饰方法：表明该方法是最终方法，**不能被重写**

  - 修饰变量：表明该变量是常量，**不能再次被赋值**

    > 常量的命名规范：如果是一个单词，所有字母大写，如果是多个单词，所有字母大写，但是中间需要使用下划线_分隔
    >
    > 修饰基本数据类型变量：其值不能被更改
    >
    > 修饰引用数据类型变量：地址值不能被更改，但是可以修改对象的属性值
    >
    > final修饰成员变量，需要在创建的时候直接赋值或者在构造方法结束之前完成赋值

  - 修饰类：表明该类是最终类，**不能被继承**

### 代码块

- 概述与分类
  - 在Java中，使用{}括起来的代码都被称为代码块
  - 分类
    - 局部代码块
      - 位置：方法中定义
      - 作用：限定变量的生命周期，及早释放，提高内存利用率
    - 构造代码块
      - 位置：类中方法外定义
      - 特点：每次构造方法执行的时候，都会执行该代码块中的代码，并且在构造方法执行前执行
      - 作用：将多个构造方法中相同的代码，抽取到构造代码块中，提高代码的复用性
    - 静态代码块
      - 位置：类中方法外定义
      - 特点：需要通过static关键字修饰，随着类的加载而加载，并且只执行一次
      - 作用：在类加载的时候做一些数据初始化的操作

### 接口

- 概述：当一个类中所有方法都是抽象方法的时候，我们就可以将其定义为接口
  			接口也是一种引用数据类型，它比抽象类还要抽象

- 意义

  - **规则**的定义
  - 程序的**扩展性**

- 定义和特点

  - 使用interface关键字：`public interface 接口名{}`
  - 接口不能实例化（创建对象）
  - 接口和类之间是实现关系，通过implements关键字表示
    `public class 类名 implements 接口名{}`
  - 接口的子类（实现类）
    要么重写接口中的所有抽象方法
    要么是抽象类
  - 支持单接口实现，也支持多实现
    `public class 类名 implements 接口名1,接口名2{}`

- 成员的特点

  - 成员变量

    只能是常量，系统会默认加入三个关键字:`public`、`static`、`final`

  - 构造方法
    接口中不存在构造方法

  - 成员方法
    只能是抽象方法（JDK7以前），系统会默认加入两个关键字：`public`、`abstract`

    > **JDK8中接口成员的特点**
    >
    > 允许接口中定义非抽象方法，但是需要使用关键字`default`修饰，这些方法就是默认方法
    >
    > 定义格式：`public default 返回值类型 方法名(参数列表){}`
    >
    > 默认方法不是抽象方法，所以不强制重写，但是可以被重写，重写的时候去掉default关键字
    >
    > public可以省略，但是default不能省略
    >
    > 如果实现了多个接口，多个接口中存在相同的方法声明，子类就必须对该方法进行重写

    > **JKD9中接口成员的特点**
    >
    > 接口中私有方法的定义格式：
    > `private 返回值类型 方法名(参数列表){}`      `private static 返回值类型 方法名(参数列表){}`

- 使用思路
  - 如果发现一个类中所有的方法都是抽象方法，那么就可以将该类，改进为一个接口
  - 涉及到了接口大面积更新方法，而不想去修改每一个实现类，就可以将更新的方法，定义为带有方法体的默认方法
  - 希望默认方法的调用更加简洁，可以考虑设计为static静态方法(需要去掉default关键字)
  - 默认方法中出现了重复的代码，可以考虑抽取出一个私有方法(需要去掉default关键字)

- 类和接口的关系
  - 类和类的关系
    继承关系，只能单继承，但是可以多层继承
  - 类和接口的关系
    实现关系，可以单实现，也可以多实现，还可以在继承一个类的同时实现多个接口
  - 接口和接口的关系
    继承关系，可以单继承，也可以多继承

### 多态

- 概述：同一个对象，在不同时刻表现出来的不同形态
- 前提
  - 要有（继承 \ 实现）关系
  - 要有方法重写
  - 要有父类引用，指向子类对象
- 成员访问特点
  - 构造方法：同继承一样，子类会通过super访问父类构造方法
  - **成员变量**：编译看（等号）左边（父类），执行看（等号）右边（父类）
  - **成员方法**：编译看（等号）左边（父类），执行看（等号）右边（子类）
- 优劣点
  - 好处：提高了程序的扩展性
    			具体体现：定义方法的时候，使用父类型作为参数，该方法就可以接收这父类的任意子类对象
  - 弊端：不能使用子类的特有功能
- 多态中的转型
  - 向上转型
    	从子到父
    	父类引用指向子类
  - 向下转型
    	从父到子
    	父类引用转为子类对象
  - 存在的风险
    - 概述：如果被转的引用类型变量，对应的实际类型和目标类型不是同一种类型，那么在转换的时候就会出现**ClassCastException**
  - **instanceof**关键字
    - 使用格式：`变量名 instanceof 类型`
      通俗的理解：判断关键字左边的变量，是否是右边的类型，返回boolean类型结果

### 内部类

- 概述：就是在一个类中定义一个类。举例：在A类的内部定义一个B类，B类就被称为内部类

#### 成员内部类

- 位置：在类的成员位置

- 创建内部类对象的格式：`外部类名.内部类名 对象名 = new 外部类对象(). new 内部类对象()`
- 内部类的访问特点
  - 内部类可以直接访问外部类的成员，包括私有
  - 外部类要访问内部类的成员，必须创建对象
- 也属于成员，可以被一些修饰符修饰
  - **private**
    私有成员内部类访问：在自己所在的外部类中创建对象访问
  - **static**
    静态成员内部类访问格式：`外部类名.内部类名 对象名 = new 外部类名.内部类名();`
    静态成员内部类中的静态方法：`外部类名.内部类名.方法名();`

#### 局部内部类

- 概述：局部内部类是在方法中定义的类，所以外界无法直接使用，需要在方法内部创建对象并使用，该类可以直接访问外部类的成员，也可以访问方法内的局部变量

- 位置：类的局部位置

#### 匿名内部类

- 概述：本质上是一个特殊的局部内部类(定义在方法内部)[使用次数远远大于成员内部类和局部内部类]

- 前提：需要存在一个接口或类

- 格式

  ```java
  new 类名或者接口名(){
      重写方法;
  }
  ```

- 理解：将继承\实现，方法重写，创建对象三个步骤放在了一步进行

- 使用场景

  当方法的形式参数是接口或者抽象类时，可以将匿名内部类作为实际参数进行传递

### Lamdba表达式

- **理解**：对于Lambda表达式，是对匿名内部类进行了优化，代码更少，关注点更加明确

- **函数式编程思想概述**
  在数学中，函数就是有输入量、输出量的一套计算方案，也就是“拿数据做操作”
  面向对象思想强调“必须通过对象的形式来做事情”
  函数式思想则尽量忽略面向对象的复杂语法：“强调做什么，而不是以什么形式去做”
  而我们要学习的Lambda表达式就是函数式思想的体现
  
- **标准格式**

  - 格式：`(形式参数) -> {代码块}`
  - 形式参数：如果有多个参数，参数之间用逗号隔开；如果没有参数，留空即可
  - `->`:由英文中画线和大于符号组成，固定写法，代表指向动作
  - 代码块：是我们具体要做的事情，也就是以前写的方法体内容

- **使用前提**

  - 有一个接口
  - 接口中有且仅有一个抽象方法

- **练习**

  ```java
  // 1.编写一个接口(ShowHandler)
  // 2.在该接口中存在一个抽象方法(show),该方法是无参数无返回值
  // 3.在测试类(ShowHandlerDemo)中存在一个方法(useShowHandler)
  //	方法的参数是ShowHandler类型的
  //	在方法内部调用了ShowHandler的show方法
  public class TestLambda{
      public static void main(String[] args){
          // 匿名内部类实现
          useShowHandler(new ShowHandler(){
              @Override
              public void show(){
                  System.out.println("我是匿名内部类中的show方法");
              }
          });
          
          // Lambda实现
          useShowHandler(() -> {System.out.println("我是匿名内部类中的show方法");});
      }
      public static void useShowHandler(ShowHandler showHandler){
          showHandler.show();
      }
  }
  
  interface ShowHandler{
      void show();
  }
  ```

  ```java
  // 1.首先存在一个接口(StringHandler)
  // 2.在该接口中存在一个抽象方法(printMessage),该方法是有参数无返回值
  // 3.在测试类(StringHandlerDemo)中存在一个方法(useStringHandler)，方法的参数是StringHandler类型的，在方法内部调用了StringHandler的printMessage方法
  public class StringHandlerDemo{
      public static void main(String[] args){
          // 匿名内部类实现
          useStringHandler(new StringHandler(){
              @Override
              public void printMessage(String msg){
                  System.out.println("我是匿名内部类." + msg);
              }
          });
          
          // Lambda实现
          useStringHandler((String msg) -> {System.out.println("我是Lambda" + msg);});
      }
      
      public static void useStringHandler(StringHandler stringHandler){
          stringHandler.printMessage("坚持学习！");
      }
  }
  
  interface StringHandler{
      void printMessage(String msg);
  }
  ```

- **省略规则**

  - 参数类型可以省略，但是有多个参数的情况下，不能只省略一个
  - 如果参数有且仅有一个，那么小括号可以省略
  - 如果代码块的语句只有一条，可以省略大括号和分号，甚至是return

- **Lambda表达式和匿名内部类的区别**
  所需类型不同

  - 匿名内部类：可以是接口，也可以是抽象类，还可以是具体类
  - Lambda：只能是接口

  使用限制不同

  - 如果接口中有且仅有一个抽象方法，可以使用Lambda表达式，也可以使用匿名内部类
  - 如果接口中多于一个抽象方法，只能使用匿名内部类，而不能使用Lambda表达式

  实现原理不同

  - 匿名内部类：编译之后，产生一个单独的.class字节码文件
  - Lambda表达式：编译之后，没有一个单独的.class字节码文件，对应的字节码会在运行的时候动态生成

## 常用API&异常

### API的基本使用

- **概述**：API(Application Programming interface)就是应用程序接口。简单来说，就是Java帮我们写好的可以直接使用的一些方法。

#### Math类

- Math包含执行基本数字运算的方法

- 没有构造方法，所有成员都是静态的(static)，可以直接通过类名调用

- 常用方法

  |                   方法名                    |                 说明                 |
  | :-----------------------------------------: | :----------------------------------: |
  |        public static int abs(int a)         |           返回参数的绝对值           |
  |     public static double ceil(double a)     |               向上取整               |
  |    public static double floor(double a)     |               向下取整               |
  |      public static int round(float a)       |               四舍五入               |
  |     public static int max(int a,int b)      |       返回两个int值中的较大值        |
  |     public static int min(int a,int b)      |       返回两个int值中的较小值        |
  | public static double pow(double a,double b) |           返回a的b次幂的值           |
  |        public static double random()        | 返回值为double的随机值   [0.0 , 1.0) |

#### System类

- 概述
  不能被实例化（不能被创建对象）

- 常用方法

  |                           方法名                            |                   说明                    |
  | :---------------------------------------------------------: | :---------------------------------------: |
  |             public static void exit(int status)             | 终止当前运行的Java虚拟机，非0表示异常终止 |
  |           public static long currentTimeMillis()            |        返回当前时间(以毫秒为单位)         |
  | arraycopy(数据源数组,起始索引,目的地数组,起始索引,拷贝个数) |                 数组copy                  |

### Object类

- 概述：每个类都可以将Object作为父类。所有类都直接或间接的继承自该类
  			直接打印一个对象就是打印这个对象的toString方法的返回值
    			Object类的toString方法得到的是对象的地址值，我们一般会对toString方法进行重写
- 构造方法:`public Object();`

#### 常用方法

|              方法名               |                            说明                            |
| :-------------------------------: | :--------------------------------------------------------: |
|     public String toString()      | 返回对象的字符串表示形式。建议所有子类重写该方法，自动生成 |
| public boolean equals(另一个对象) | 比较对象是否相等。默认比较地址，重写可以比较内容，自动生成 |

#### 面试题

```java
public class InterviewTest{
    public static void main(String[] args){
        String s1 = "abc";
        StringBuilder sb = new StringBuilder("abc");
        System.out.println(s1.equals(sb));		// false
        // 此时调用的是String类中的equals方法
		// 会先判断是否是字符串，若不是字符串则不会比较属性值，直接返回false
        System.out.println(sb.equals(s1));		// false
        // 此时调用的是StringBuilder中的equals方法，StringBuilder并没有该方法，则继承Object中的equals方法
        // 即比较地址值，返回false
    }
}
```

#### Objects

- 无构造方法，但所有成员方法都是静态方法(static)，可以直接根据类名调用

- 常用方法

  |                     方法名                     |                          说明                          |
  | :--------------------------------------------: | :----------------------------------------------------: |
  |      public static String toString(对象)       |             返回参数中对象的字符串表示形式             |
  | public static String toString(对象,默认字符串) | 返回对象的字符串表示形式，如果对象为空，返回默认字符串 |
  |       public static Boolean isNull(对象)       |                    判断对象是否为空                    |
  |      public static Boolean nonNull(对象)       |                   判断对象是否不为空                   |

### BigDecimal类

#### 构造方法

| 方法名                 | 说明         |
| ---------------------- | ------------ |
| BigDecimal(double val) | 参数为double |
| BigDecimal(String val) | 参数为String |

#### 常用方法

作用：可以用来精确计算（如果想要精确运算，请使用字符串构造）

| 方法名                                                       | 说明 |
| ------------------------------------------------------------ | ---- |
| public BigDecimal add(另一个BigDecimal对象)                  | 加法 |
| public BigDecimal subtract(另一个BigDecimal对象)             | 减法 |
| public BigDecimal multiply(另一个BigDecimal对象)             | 乘法 |
| public BigDecimal divide(另一个BigDecimal对象)               | 除法 |
| ==public BigDecimal divide(另一个BigDecimal对象,精确几位,舍入模式)== | 除法 |

> 舍入模式：
>
> 进一法：**ROUND_UP**
> 去尾法：**ROUND_FLOOR**
> 四舍五入：**ROUND_HALE_UP**

### Integer类

- 概述：Integer类包装一个对象中的原始类型int的值。（基本类型包装类）

#### 包装类

- 将基本数据类型封装为对象的好处在于可以在对象中定义更多的功能方法操作该数据
  常用的操作之一：用于基本数据类型与字符串之间的转换

  > | 基本数据类型 |    包装类     |
  > | :----------: | :-----------: |
  > |     byte     |     Byte      |
  > |    short     |     Short     |
  > |   ==int==    |  ==Integer==  |
  > |     long     |     Long      |
  > |    float     |     Float     |
  > |    double    |    Double     |
  > |   ==char==   | ==Character== |
  > |   boolean    |    Boolean    |

#### Integer类的使用

- **构造方法**
  `public Integer(int value)`		根据int创建Integer对象**(过时)**
  `public Integer(String s)`			根据String值创建Integer对象**(过时)**
  `public static Integer valueof(int i)`			返回表示指定的int值的Integer实例
  `public static Integer valueof(String s)`			返回一个保存指定值的Integer对象String

- **自动装箱**

  - 装箱：把一个基本数据类型变成与之对应的包装类
  - 自动：Java底层会帮我们自动的调用valueof方法
  - 使用格式：`Integer i1 = 100;`

- **自动拆箱**

  - 拆箱：把一个包装类型，变成对应的基本数据类型
  - 使用格式：`int i - i1;`		i1为Integer对象

- **成员方法**
  `static int parseInt(String s)`			将字符串类型的整数变成int类型的整数

  >```java
  >// int 转换为 String
  >// 方式一：+ ""
  >int i1 = 100;
  >String s1 = i1 + "";
  >
  >// 方式二：可以调用String类中的valueof方法
  >String s2 = String.valueof(i1);
  >```

- **练习**

  ```java
  // 案例：字符串中数据的处理
  // 需求：有一个字符串："91 27 46 38 50"，把其中的每一个数存到int类型的数组中
  public class MyIntegerDemo{
      public static void main(String[] args){
          String s = "91 27 46 38 50";
          // 获取字符串中的每一个数字
          String[] strArr = s.split(" ");
          // 创建一个int类型数组
          int[] numberArr = new int[strArr.length];
          // 把strArr中的数据进行类型转换并存入到int数组中
          for(int i = 0; i < strArr.length; i++){
              int number = Integer.parseInt(strArr[i]);
              numberArr[i] = number;
          }
          // 遍历int类型的数组
          for(int i = 0; i < numberArr.length; i++){
              System.out.println(numberArr[i]);
          }
      }
  }
  ```

### 数组的高级操作-1

- 基本查找：根据索引，遍历查找相应的元素

#### 二分查找

- 前提：数组的元素按照大小、顺序排列

- 每次去掉一半的查找范围

- 步骤

  - 定义两个变量，表示要查找的范围。默认min=0，max = 最大索引
  - 循环查找，但是min <= max
  - 计算出mid的值
  - 判断mid位置的元素是否为要查找的元素，如果是直接返回对应索引
  - 如果要查找的值在mid左半边，那么min值不变，max = mid - 1，继续下次循环查找
  - 如果要查找的值在mid右半边，那么max值不变，max = mid + 1，继续下次循环查找

  - 当min > max时，表示要查找的元素在数组中不存在，返回-1

    ```java
    public class MyBinarySearchDemo{
        public static void main(String[] args) {
            int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
            int number = 10;
            int index = binarySearchForIndex(arr, number);
            System.out.println(index);
        }
    
        private static int binarySearchForIndex(int[] arr, int number) {
            // 定义查找的范围
            int min = 0;
            int max = arr.length - 1;
            // 循环查找  min <= max
            while (min <= max) {
                // 计算中间位置
                int mid = (min + max) >> 1;            // 右移一位，也是除以二的意思
                // mid指向的元素 > number
                if (arr[mid] > number) {
                    // 表示要查找的元素在左边
                    max = mid - 1;
                }
                // mid指向的元素 < number
                else if (arr[mid] < number) {
                    // 表示要查找的元素在右边
                    min = mid + 1;
                } else {
                    // mid指向的元素 == number
                    return mid;
                }
            }
            // 如果min大于了max就表示元素不存在，返回-1
            return -1;
        }
    }
    ```

#### 冒泡排序

- 排序：将一组数据按照固定的规则进行排列
- 冒泡排序：相邻的数据两两比较，小的放前面，大的放后面。
- 步骤
  - 相邻的元素两两比较，大的放右边，小的放左边，找到最大值
  - 第一次循环结束，最大值已经找到，在数组的最右边
  - 下一次只要在剩余的元素中找最大值就可以了
- 如果有n个数据进行排序，总共需要比较n - 1次
- 每一次比较完毕，下一次的比较就会少一个数据参与

```java
public class MyBubbleSortDemo{
    public static void main(String[] args){
        int[] arr = {3, 5, 2, 1, 4};
        bubbleSort(arr);
        printArr(arr);
    }
    
    private static void bubbleSort(int[] arr){
        // 循环排序
        // 外层循环控制次数，比数组的长度少一次
        for(int i = 0; i < arr.length - 1; i++){
            // 内存循环就是实际比较的次数
            for(int j = 0; j < arr.length - 1 - i; j++){
                // -1为了让数组不越界，-i 是每轮结束后都会减少比较
                if(arr[j] > arr[j+1]){
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
    
    private static void printArr(int[] arr){
        // 循环遍历
        for(int i = 0; i < arr.length; i++){
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }
}
```

### 递归

- 概述：以编程角度来看，递归指的是方法定义中调用方法本身的现象

- 解决问题的思路：把一个复杂的问题层层转化为一个**与原问题相似的规模较小**的问题来求解，递归策略只需**少量的程序**就可描述出解题过程所需要的多次重复计算

- 递归解决问题要有两个内容

  - 递归出口：否则会出现内存溢出
  - 递归规则：与原问题相似的规模较小的问题

- 案例

  ```java
  // 求1~100的和（递归实现）
  public class MyFactorialDemo1{
      public static void main(String[] args){
          int sum = getSum(100);
          System.out.println(sum);
      }
      
      private static int getSum(int i){
          if(i == 1){
              return 1;
          }else{
              return i + getSum(i - 1);		// i + (i - 1)的和
          }
      }
  }
  ```

  ```java
  // 需求：用递归求5的阶乘，并把结果在控制台输出
  public class MyFactorialDemo2{
      public static void main(String[] args){
          int result = getJc(5);
          System.out.println(result);
      }
      
      private static int getJc(int i){
          // 出口
          if(i == 1){
              return 1;
          }else{
              // 规则（递归下一次调用的，一定更接近出口）
              return i * getJc(i - 1);
          }
      }
  }
  ```

### 数组的高级操作-2

#### 快排

- 冒泡排序算法中，一次循环结束，就相当于确定了当前的最大值，也能确定最大值在数组中应存入的位置。

- 快速排序算法中，每一次递归时以第一个数为基准数，找到数组中所有比基准数小的。再找到所有比基准数大的。小的全部放左边，大的全部放右边，确定基准数的正确位置

  ```java
  public class MyQuiteSortDemo{
      public static void main(String[] args) {
          int[] arr = {6, 1, 2, 7, 9, 3, 4, 5, 10, 8};
          quiteSort(arr, 0, arr.length - 1);
          for (int i = 0; i < arr.length; i++) {
              System.out.print(arr[i] + " ");
          }
      }
  
      private static void quiteSort(int[] arr, int left, int right) {
          if (right < left) {
              return;
          }
  
          // 记录两个值
          int left0 = left;
          int right0 = right;
  
          // 计算出基准数
          int baseNumber = arr[left0];
          while (left != right) {
              // 1.从右开始找比基准数小的
              while (arr[right] >= baseNumber && right > left) {
                  right--;
              }
              // 2.从左开始找比基准数大的
              while (arr[left] <= baseNumber && right > left) {
                  left++;
              }
              // 3.交换两个值的位置
              int temp = arr[left];
              arr[left] = arr[right];
              arr[right] = temp;
          }
          // 4. 基准数归位
          int temp = arr[left];
          arr[left] = arr[left0];
          arr[left0] = temp;
  
          // 再次递归调用方法
          quiteSort(arr, left0, left - 1);
          quiteSort(arr, left + 1, right0);
      }
  }
  ```

#### Arrays

- Arrays类包含用于操作数组的各种方法

  |                     方法名                      |                说明                |
  | :---------------------------------------------: | :--------------------------------: |
  |     public static String toString(int[] a)      | 返回指定数组的内容的字符串表示形式 |
  |        public static void sort(int[] a)         |     按照数字顺序排列指定的数组     |
  | public static int binarySearch(int[] a,int key) |   利用二分查找返回指定元素的索引   |

  > public static int binarySearch(int[] a,int key) 
  > 			1.数组必须有序
  > 			2.如果查找的元素存在，那么返回的是这个元素实际的索引
  > 			3.如果要查找的元素不存在，那么返回的是(-插入点-1)
  > 						插入点：如果这个元素在数组中，他应该在的索引位置

### 时间日期类

- 世界标准时间：格林尼治时间/格林威治时间，简称GMT
- 中国标准时间：世界标准时间 ==+ 8小时==
- 时间换算公式
  1秒 = 1000毫秒
  1毫秒 = 1000微秒
  1微秒 = 1000纳秒
- 计算机中的时间原点：1970年1月1日 00:00:00

#### Date类

- Date代表了一个特定的时间，精确到毫秒

- 构造方法

  |         方法名         |                             说明                             |
  | :--------------------: | :----------------------------------------------------------: |
  |     public Date()      |       创建一个Date对象，表示默认时间(电脑中的当前时间)       |
  | public Date(long data) | 创建一个Date对象，表示指定时间(从计算机时间原点开始，过了指定毫秒后的时间) |

- 常用成员方法

  |             方法名             |         说明         |
  | :----------------------------: | :------------------: |
  |     public long getTime()      | 获取时间对象的毫秒值 |
  | public void setTime(long time) | 设置时间，传递毫秒值 |

#### SimpleDateFormat类

- SimpleDateFormat可以对Date对象，进行**格式化和解析**
  ==格式化==：Date对象      \==\=\=》        2021年1月1日 00:00:00
  ==解析==：2021年1月1日 00:00:00      \===\=》        Date对象

- **常用的模式字母及对应关系**
  y   -----   年                     M ----- 月                        d ----- 日
  H   -----   时                     m ----- 分                        s ----- 秒
  2021-01-01 00:00:00   -------------   yyyy-MM-dd HH:mm:ss

- **构造方法**

  |                 方法名                  |                   说明                   |
  | :-------------------------------------: | :--------------------------------------: |
  |        public SimpleDateFormat()        |  构造一个SimpleDateFormat,使用默认格式   |
  | public SimpleDateFormat(String pattern) | 构造一个SimpleDateFormat，使用指定的格式 |

- **成员方法**

  |                方法名                 |                 说明                 |
  | :-----------------------------------: | :----------------------------------: |
  | public final String format(Date date) |    将日期格式化成日期/时间字符串     |
  |   public Date parse(String source)    | 从给定字符串的开始解析文本以生成日期 |

### JDK8时间类

- **JDK8新增日期类**
  **Date**分为==LocalDate==、==LocalTime==、==LocalDateTime==
  LocalDate   表示日期（年月日）			2021年11月11日
  LocalTime   表示日期（时分秒）		 11:11:11
  LocalDateTime   表示日期 + 时间（年月日时分秒）			2021年11月11日 11:11:11

#### LocalDateTime类

- **LocalDateTime创建方法**

  |                      方法名                       |                       说明                        |
  | :-----------------------------------------------: | :-----------------------------------------------: |
  |         public static LocalDateTime now()         |                获取当前的系统时间                 |
  | public static LocalDateTime of(年,月,日,时,分,秒) | 使用指定年月日和时分秒初始化一个LocalDateTime对象 |

- **LocalDateTime获取方法**

  |             方法名              |           说明            |
  | :-----------------------------: | :-----------------------: |
  |      public int getYear()       |          获取年           |
  |   public int getMonthValue()    |      获取月份(1-12)       |
  |   public int getDayOfMonth()    | 获取月份中的第几天(1-31)  |
  |    public int getDayOfYear()    | 获取一年中的第几天(1-366) |
  | public DayOfWeek getDayOfWeek() |         获取星期          |
  |     public int getMinute()      |         获取分钟          |
  |      public int getHour()       |         获取小时          |

- **LocalDateTime转换方法**

  |             方法名             |          说明           |
  | :----------------------------: | :---------------------: |
  | public LocalDate toLocalDate() | 转换为一个LocalDate对象 |
  | public LocalTime toLocalTime() | 转换为一个LocalTime对象 |

- **LocalDateTime格式化和解析**

  |                          方法名                           |                             说明                             |
  | :-------------------------------------------------------: | :----------------------------------------------------------: |
  |              public String format(指定格式)               |           把一个LocalDateTime格式化成为一个字符串            |
  |   public LocalDateTime parse(准备解析的字符串,解析格式)   |         把一个日期字符串解析为一个LocalDateTime对象          |
  | public static DateTimeFormatter ofPattern(String pattern) | 使用指定的日期模板获取一个日期格式化器Date TimeFormatter对象 |

- **LocalDateTime增加或者减少时间的方法**

  |                     方法名                     |              说明              |
  | :--------------------------------------------: | :----------------------------: |
  |   public LocalDateTime plusYears(long years)   | 添加（正数）或者减（负数）去年 |
  |  public LocalDateTime plusMonths(long months)  |         添加或者减去月         |
  |    public LocalDateTime plusDays(long days)    |         添加或者减去日         |
  |   public LocalDateTime plusHours(long hours)   |         添加或者减去时         |
  | public LocalDateTime plusMinutes(long minutes) |         添加或者减去分         |
  | public LocalDateTime plusSeconds(long seconds) |         添加或者减去秒         |
  |   public LocalDateTime plusWeeks(long weeks)   |         添加或者减去周         |

  `public LocalDateTime minusYears(long years)`				减去或添加年，和上边方法相反
  还有其他和上述方法类似的减去或添加方法

- **LocalDateTime修改方法**

  | 方法名                                              | 说明                             |
  | --------------------------------------------------- | -------------------------------- |
  | public LocalDateTime withYear(int year)             | 直接修改年                       |
  | public LocalDateTime withMonth(int month)           | 直接修改月                       |
  | public LocalDateTime withDayOfMonth(int dayOfMonth) | 直接修改日期（一个月中的第几天） |
  | public LocalDateTime withDayOfYear(int dayOfYear)   | 直接修改日期（一年中的第几天）   |
  | public LocalDateTime withHour(int hour)             | 直接修改小时                     |
  | public LocalDateTime withMinute(int minute)         | 直接修改分钟                     |
  | public LocalDateTime withSecond(int second)         | 直接修改秒                       |

#### 时间间隔类

- **Period类**

  | 方法名                                          | 说明                 |
  | ----------------------------------------------- | -------------------- |
  | public static Period between(开始时间,结束时间) | 计算两个“时间”的间隔 |
  | public int getYears()                           | 获得这段时间的年数   |
  | public int getMonths()                          | 获得次期间的月数     |
  | public int getDays()                            | 获得此期间的天数     |
  | public long toTotalMonths()                     | 获取此期间的总月数   |

- **Duration类**

  | 方法名                                           | 说明                 |
  | ------------------------------------------------ | -------------------- |
  | public static Durationbetween(开始时间,结束时间) | 计算两个“时间”的间隔 |
  | public long toSeconds()                          | 获得此时间间隔的秒   |
  | public int toMillis()                            | 获得此时间间隔的毫秒 |
  | public int toNanos()                             | 获得此时间间隔的纳秒 |

### 异常

- 异常：就是程序出现了不正常的情况。程序在执行的过程中，出现的非正常的情况，最终会导致JVM的非正常停止。
  ==注意：==语法错误不算在异常体系中

#### JVM的默认处理方案

如果程序出现了问题，我们没有做任何处理，最终JVM会做默认的处理

- 把异常的名称，异常原因及异常出现的位置等信息输出在了控制台
- 程序停止执行（哪里出现异常就在哪里停止程序的运行）

#### throws

- 格式:`throws 异常类名;`
  ==注意==：这个格式是写在方法的定义处，表示声明一个异常。

  > 指告诉==调用者==，在调用的时候可能出现这样的异常，如果方法中没有出现异常，正常执行。如果真的出现了异常，则是交给==调用者==处理，若调用者没有处理，则最终还是交给==JVM虚拟机==处理。
  >
  > 如果声明的异常是一个运行时异常，那么声明的代码可以省略
  > 如果声明的异常是一个编译时异常，则必须要在方法后面进行显示声明

#### throw

- 格式：`throw new 异常();`
  ==注意==：这个格式是在方法内，表示当前代码手动抛出一个异常，下面的代码不再执行了。

- throw和throws的区别

  |                     throws                     |                   throw                    |
  | :--------------------------------------------: | :----------------------------------------: |
  |        用在方法声明后面，跟的是异常类名        |        用在方法内，跟的是异常对象名        |
  | 表示声明异常，调用该方法有可能会出现这样的异常 | 表示手动抛出异常对象，由方法体内的语句处理 |

- 意义
  1. 在方法中，当传递的参数有误，没有继续运行下去的意义了，则采取抛出处理，表示让该方法结束运行。
  2. 告诉调用者方法中出现了问题。

#### try...catch...

- 格式：

  ```java
  try{
      可能出现异常的代码;
  }catch(异常类名 变量名){
      异常的处理代码;
  }
  ```

- ==优点==：可以让程序继续向下执行。
- 常见问题
  - 如果try中没有问题，会把try中代码全部执行完毕，但不会执行catch内的代码
  - 当try中出现问题，直接跳转到catch语句中，try下面的语句就不会再执行，当catch内的语句全部执行完毕，会继续执行下面代码
  - 出现多个异常，就需要写多个catch语句。如果多个异常之间存在子父类关系，那么父类一定要写在下面。

#### 异常的成员方法

| 方法名                        | 说明                                 |
| ----------------------------- | ------------------------------------ |
| public String getMessage()    | 返回此throwbale的详细消息字符串      |
| public String toString()      | 返回此可抛出的简短描述               |
| public void printStackTrace() | 把异常的信息输出在控制台（红色字体） |

#### 两种处理异常方式小结

- 抛出 throw throws
  - 在方法中，当传递的参数有误，没有继续执行下去的意义了，则采取抛出处理，表示让该方法结束运行
  - 告诉调用者出现了问题
- 捕获 try...catch...
  - 能让代码继续运行下去

- 案例：键盘录入数据

  ```java
  // 需求：
  // 键盘录入学生的姓名和年龄，其中年龄为18-25岁
  // 超出这个范围是异常数据不能赋值，需要重新录入，一直录入到正确为止
  public class ExceptionDemo{
      public static void main(String[] args){
          Student s = new Student();
          
          Scanner sc = new Scanner(System.in);
          System.out.print("请输入姓名：");
          String name = sc.nextLine();
          String name = sc.nextLine();
          while(true){
              System.out.print("请输入年龄：");
          	String ageStr = sc.nextLine();
          	try{
                  int age = Integer.parseInt(ageStr);
              	s.setAge(age);
                  break;
              }catch(NumberFormatException e){
                  System.out.println("请输入一个整数");
                  continue;
              }catch(RuntimeException e){
                  System.out.println("请输入一个符合范围的年龄");
                  continue;
              }
          	
          }
          System.out.println(s);
      }   
  }
  ```

  ```java
  // Student类
  public class Student{
      private String name;
      private int age;
      
      public Student();
      
      public void setName(String name){
          this.name = name;
      }
      public void setAge(int age){
          if(age >= 18 && age <= 25){
              this.age = age;
          }else{
              throw new RuntimeException("年龄超出了范围");
          }
      }
      public String getName(){
          return name;
      }
      public int getAge(){
          return age;
      }
      public String toString() {
          return "Student{" +
                  "name='" + name + '\'' +
                  ", age=" + age +
                  '}';
      }
  }
  ```

#### 自定义异常

- 目的：为了让异常信息更加见名知意
- 步骤
  1. 定义异常类
  2. 写继承关系
  3. 完善构造方法（空参/有参）

## 集合

### Collection

#### 集合和数组的对比

- 数组的长度不可变，集合的长度可变
- 数组可以存储基本数据类型和引用数据类型
  集合只能存储引用数据类型。如果要存储基本数据类型，需要存储对应的包装类

#### 集合体系结构

- 单列结构
  List结构：可出现重复元素
  Set结构：不可以出现重复的元素
- 双列结构
  ![](E:\Typora\学习笔记\images\集合的体系结构.jpeg)

#### Collection集合概述

- 是单列集合的顶层接口，它表示一组对象，这些对象也成为Collection的元素
- JDK不提供此接口的任何直接实现，它提供更具体的子接口（如Set和List）实现

#### 创建Collection集合的对象

- 多态的方式
- 具体的实现类ArrayList

#### 常见成员方法

| 方法名                     | 说明                               |
| -------------------------- | ---------------------------------- |
| boolean add(E e)           | 添加元素                           |
| boolean remove(Object o)   | 从集合中移除指定的元素             |
| boolean removeif(Object o) | 根据条件进行删除                   |
| void clear()               | 清空集合                           |
| boolean contains(Object o) | 判断集合中是否存在指定的元素       |
| boolean isEmpty()          | 判断集合是否为空                   |
| int size()                 | 集合的长度，也就是集合中元素的个数 |

#### Collection集合的遍历

- Iterator：迭代器，集合的专用遍历方式
- Iterator<E> iterator():返回集合中的迭代器对象，该迭代器对象默认指向当前集合的0索引
- Iterator中的常用方法
  - `boolean hasNext()`：判断当前位置是否有元素可以被取出
  - `E next()`:获取当前位置的元素，并将迭代器对象移向下一个索引位置
- 步骤：
  1. 获取迭代器的对象:`Iterator<E> it = list.iterator();`
  2. 利用迭代器的成员方法进行遍历
- 迭代器原理

#### 增强for循环

- 增强for：简化数组和Collection集合的遍历

  - 它是JDK5之后出现的，其内部原理是一个Iterator迭代器
  - 实现Iterable接口的类才可以使用迭代器和增强for

- 格式

  ```java
  for(元素数据类型 变量名 : 数组或者Collection集合){
      // 在此处使用变量即可，该变量就是元素
  }
  // 数据类型一定是集合或者数组元素的类型
  // 变量名在循环的过程中，依次表示集合或者数组中的每一个元素
  ```

- 注意点：在增强for中，修改第三方变量的值不会影响到集合中的元素
- **三种循环的使用场景**
  - 如果需要操作索引，使用普通for循环
  - 如果在遍历的过程中需要删除元素，请使用迭代器
  - 如果仅仅想遍历，那么使用增强for

#### 案例

```java
// 需求：创建一个Collection集合存储学生对象的集合，存储3个学生对象，使用程序实现在控制台遍历该集合

// ----------Student类--------------------
public class Student{
    private String name;
    private int age;

    public Student() {
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}


// ----------Test类--------------------
import java.util.ArrayList;
import java.util.Iterator;

public class test {
    public static void main(String[] args) {
        ArrayList<Student> list = new ArrayList<>();

        Student s1 = new Student("张三", 23);
        Student s2 = new Student("李四", 16);
        Student s3 = new Student("王五", 31);
        list.add(s1);
        list.add(s2);
        list.add(s3);

        // 迭代器遍历
        Iterator<Student> it = list.iterator();
        while (it.hasNext()) {
            Student s = it.next();
            System.out.println(s);
        }

        System.out.println("----------------------");

        // 增强for遍历
        for (Student s : list) {
            System.out.println(s);
        }
    }
}

```

### List与LinkedList

#### 概述

- 有序集合，这里的有序指的是存取顺序
- 用户可以精确控制列表中每个元素的插入位置，用户可以通过整数索引访问元素，并搜索列表中的元素
- 与Set集合不同，列表通常允许重复的元素

#### 常用方法

|             方法名             |                  说明                  |
| :----------------------------: | :------------------------------------: |
| void add(int index, E element) |   在此集合中的指定位置插入指定的元素   |
|      E remove(int index)       | 删除指定索引处的元素，返回被删除的元素 |
|  E set(int index, E element)   | 修改指定索引处的元素，返回被修改的元素 |
|        E get(int index)        |          返回指定索引处的元素          |

#### 数据结构

- 数据结构是计算机存储、组织数据的方式。是指相互之间存在一种或多种特定关系的数据元素的集合。通常情况下，精心选择的数据结构可以带来更高的运行或者存储效率

##### 栈

- 栈是一种数据**先进后出**的模型
- 只允许在一端进行操作
- 数据进栈的过程称为**压/进栈**
- 数据进栈的过程称为**弹/出栈**

##### 队列

- 队列是一种**先进先出**的模型
- 在两端进行操作
- 数据进栈的过程称为**入队**
- 数据进栈的过程称为**出队**

##### 数组

- 数组是一个**查询快、增删慢**的模型

- 查询数据通过地址值和索引定位，查询任意数据耗时相同，**查询速度快**
- 删除数据时，要将原始数据删除，同时后面每个数据前移，**删除效率低**
- 添加数据时，添加位置后的每个数据后移，再添加元素，**添加效率极低**

##### 链表

- 链表是一个**查询慢、增删快**的模型（对比数组）

#### List常用实现类

- ArrayList：底层数据结构是数组，**查询快、增删慢**

- LinkedList：底层数据结构是链表，**查询慢、增删快**

  - 特有功能

    |          方法名           |               说明               |
    | :-----------------------: | :------------------------------: |
    | public void addFirst(E e) |    在该列表开头插入指定的元素    |
    | public void addLast(E e)  |  将指定的元素追加到此列表的末尾  |
    |    public E getFirst()    |     返回此列表中的第一个元素     |
    |    public E getLast()     |    返回此列表中的最后一个元素    |
    |  public E removeFirst()   |  从此列表中删除并返回第一个元素  |
    |   public E removeLast()   | 从此列表中删除并返回最后一个元素 |


### 泛型

- 泛型：是JDK5中的特性，它提供了编译时类型安全检测机制
- 泛型的好处：
  - 把运行时期的问题提前到了编译期间
  - 避免了强制类型转换

#### 泛型的使用

- 类后面     --------------->      泛型类
- 方法声明上     --------------->      泛型方法
- 接口后面     --------------->      泛型接口

  > 使用泛型时，只能是引用数据类型

#### 泛型类

- 如果一个类后面有`<E>`，表示这个类是一个泛型类
- 在创建泛型类对象时，必须要给这个泛型确定具体的数据类型
- 泛型的定义格式：
  - `<类型>`：指定一种类型的格式
    					尖括号里面可以任意书写，按照变量的定义规则即可。一般只写一个字母。
          					比如：`<E>、<T>、<Q>、<K,M>`

- 泛型类的定义格式：`修饰符 class 类名<类型>{ }`

  ```java
  public class MyGenericityClass<E> {
  	private E element;
  
  	public E getElement() {
  		return element;
  	}
  
  	public void setElement(E element) {
  		this.element = element;
  	}
  
  	@Override
  	public String toString() {
  		return "MyGenericityClass [element=" + element + "]";
  	}
  	
  }
  
  ```

#### 泛型方法

- 定义格式：`修饰符 <类型> 返回值类型 方法名(类型 变量名){ }`

- 范例：`public <T> void show(T t){ }`

  ```java
  // 定义一个泛型方法，传递一个集合和四个元素，将元素添加到集合中并返回
  public class GenericityMethod{
      public static void main(String[] args){
          addElement(new ArrayList<String>, "a", "b", "c", "d");
      }
      
      public static <T> ArrayList<T> addElement(ArrayList<T> list, T t1, T t2, T t3, T t4){
          list.add(t1);
          list.add(t2);
          list.add(t3);
          list.add(t4);
          return list;
      }
  }
  ```

#### 泛型接口

- 使用方式

  - 实现类也不给泛型
  - 实现类确定具体的数据类型

- 泛型接口的定义格式：`修饰符 interface 接口名<类型>{ }`

  ```java
  public class GenericityInterface{
  	public static void main(String[] args){
  		GenericityImpl<String> genericity = new GenericityImpl<>();
  		genericity.method("ccccccc");
  	}
  }
  
  interface Genericity<E> {
  	public abstract void method(E e);
  }
  
  
  class GenericityImpl<E> implements Genericity<E>{
  	public void method(E e){
  		System.out.println(e);
  	}
  }
  ```

#### 通配符

- 类型通配符:`<?>`

- ArrayList<?>：表示元素类型未知的ArrayList，它的元素可以匹配任何的类型

  - 但是并不能把元素添加到ArrayList中了，获取出来的也是父类类型

- 类型通配符上限：`<? extends 类型>`

  - 比如：`ArrayList<? extends Number>`:它表示的类型是Number或者其子类型

- 类型通配符下限：`<? super 类型>`

  - 比如：`ArrayList<? super Number>`：他表示传进来的类型可以是Number类型，也可以是Number的父类类型

  ```java
  import java.util.ArrayList;
  
  public class tongpeifu {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		ArrayList<Integer> list1 = new ArrayList<>();
  		ArrayList<String> list2 = new ArrayList<>();
  		list1.add(11);
  		list2.add("ssacs");
  		printList(list1);
  		printList(list2);
  	}
  
  	private static void printList(ArrayList<?> list) {
  		// TODO Auto-generated method stub
  		System.out.println(list);
  		
  	}
  }
  
  ```

### Set&TreeSet

- Set集合概述和特点

  - 可以去除重复
  - 存取顺序不一致
  - 没有带索引的方法，所以不能使用普通for遍历循环，也不能通过索引来获取、删除Set集合里面的元素

- Set集合练习

  ```java
  public class MySet{
      public static void main(String args[]){
          Set<String> set = new TreeSet<>();
          set.add("ccc");
          set.add("aaa");
          set.add("aaa");
          set.add("bbb");
          // 迭代器遍历
          Iterator<String> it = set.iterator();
          while(it.hasNext()){
              String s = it.next();
              System.out.println(s);
          }
          
          System.out.println("---------------------------");
          
          // 增强for遍历
          for(String s:set){
              System.out.println(s);
          }
      }
  }
  ```

#### TreeSet

- 特点
  - 不包含重复元素的集合
  - 没有带索引的方法
  - ==可以将元素按照规则进行排序==(使用TreeSet时，要制定排序规则)

- 自然排序Comparable的使用

  - 使用**空参构造**创建TreeSet集合

  - 自定义的Student类实现**Comparable**接口

  - 重写里面的**compareTo**方法

    ```java
    @Override
    public int compareTo(Student o){
        int result = this.age - o.age;
        return result;
    }
    ```

  - 原理

    - 如果返回值为负数，表示当前存入的元素是较小值，存左边
    - 如果返回值为0，表示当前存入的元素跟集合中元素重复了，不存
    - 如果返回值为正数，表示当前存入的元素是较大值，存右边

- 比较器排序Comparator的使用

  - TreeSet的带参构造方法使用的是**比较器排序**对元素进行排序的

  - 比较器排序，就是让集合构造方法接收Comparator的实现类对象，重写**compare**(T o1, T o2)方法

  - 重写方法时，一定要注意排序规则必须要按照要求的主要条件和次要条件来写

    ```java
    @Override
    public int compare(Teacher o1, Teacher o2){
        // o1表示现在要存入的那个元素
        // o2表示已经存入到集合中的元素
        
        
        // 主要条件
        int result = o1.getAge() - o2.getAge();
        // 次要条件
        result = result == 0 ? o1.getName().compareTo(o2.getName()) : result;
        return result;
    }
    ```

- 两种比较方式小结
  - 自然排序：自定义类实现Comparable接口，重写compareTo方法，根据返回值进行排序
  - 比较器排序：创建TreeSet对象的时候传递Comparator的实现类对象，重写compare方法，根据返回值进行排序
  - **在使用的时候，默认使用自然排序，当自然排序不满足现在的需求时，使用比较排序**

### 数据结构&平衡二叉树

- 二叉树
- 二叉查找树
  - 二叉查找树，又称二叉排序树或者二叉搜索树
  - 特点
    - 每一个节点上最多有两个子节点
    - 每一个节点的左子节点都是小于自己的
    - 每一个节点的右子节点都是大于自己的
- 平衡二叉树
  - 二叉树左右两个子树的高度差不超过1
  - 任意节点的左右两个子树都是一颗平衡二叉树
  - 左旋
    - 触发时机：当添加一个节点后，可能已经破坏平衡，就会触发旋转机制
    - 左旋就是将根节点的右侧往左拉，原先的右子节点变成新的父节点，并把多余的左子节点出让，给已经降级的根节点当右子节点
  - 右旋：将根节点的左侧往右拉，左子节点变成了新的父节点，并把多余的右子节点出让，给已经降级的根节点当左子节点

### 红黑树&HashSet

#### 红黑树

- 红黑树是一种自平衡的二叉查找树，是计算机科学中用到的一种数据结构，又叫平衡二叉B树

- 它是一种特殊的二叉查找树，红黑树的每一个节点上都有存储位表示节点的颜色

- ==每一个节点可以是红或者黑==；红黑树==不是高度平衡的==，它的平衡是通过“红黑规则”进行实现的

- 红黑规则
  - 每一个节点或是红色的，或者是黑色的
  - 根节点必须是黑色
  - 如果一个节点没有子节点或者父节点，则该节点相应的指针属性值为Nil，这些Nil视为叶节点，每个叶节点(Nil)是黑色的
  - 如果某一个节点是红色，那么它的子节点必须是黑色（不能出现两个红色节点相连的情况）
  - 对每一个节点，从该节点到其所有后代叶节点的简单路径上，均包含相同数目的黑色节点
  
- 添加节点
  - 添加节点的颜色，可以是红色的，也可以是黑色的
  - 添加节点时，默认颜色为红色效率更高
  - 当添加的节点为根节点时，直接变为黑色
  - 当其父节点为根节点时，则不需要做任何操作
  - 其父节点为红色，叔叔节点也是红色
    - 将父节点设为黑色，将叔叔节点也设为黑色
    - 将祖父节点设为红色
    - 如果祖父节点为根节点，则将根节点再次变为黑色
  - 其父节点为黑色，不需要进行任何操作
  - 其父节点为红色，叔叔节点也是黑色
    - 将父节点设为黑色
    - 将祖父节点设为红色
    - 以祖父节点为支点进行旋转
  
- 练习：创建3个学生对象，属性为姓名，语数英成绩，按照总分从小到大顺序打印到控制台

  ```java
  // Student类
  
  public class Student implements Comparable<Student>{
  	private String name;
  	private int chinese;
  	private int english;
  	private int math;
  	
  	public Student(String name, int chinese, int english, int math) {
  		super();
  		this.name = name;
  		this.chinese = chinese;
  		this.english = english;
  		this.math = math;
  	}
  	public Student() {
  		super();
  	}
  	
  	public String getName() {
  		return name;
  	}
  	public void setName(String name) {
  		this.name = name;
  	}
  	public int getChinese() {
  		return chinese;
  	}
  	public void setChinese(int chinese) {
  		this.chinese = chinese;
  	}
  	public int getEnglish() {
  		return english;
  	}
  	public void setEnglish(int english) {
  		this.english = english;
  	}
  	public int getMath() {
  		return math;
  	}
  	public void setMath(int math) {
  		this.math = math;
  	}
  	public int getSum(){
  		int res;
  		res = chinese + math + english;
  		return res;
  	}
  	@Override
  	public String toString() {
  		return "Student [name=" + name + ", chinese=" + chinese + ", english=" + english + ", math=" + math + "]" + "总分为：" + getSum();
  	}
  	@Override
  	public int compareTo(Student o) {
  		// TODO Auto-generated method stub
  		int res = this.getSum() - o.getSum();
  		res = res == 0 ? this.getChinese() - o.getChinese() : res;
  		res = res == 0 ? this.getMath() - o.getMath() : res;
  		res = res == 0 ? this.getName().compareTo(o.getName()) : res;
  		return res;
  	}
  }
  
  ```

  ```java
  // 测试类
  
  import java.util.TreeSet;
  
  public class Test {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		TreeSet<Student> stu = new TreeSet<>();
  		Student s1 = new Student("李四", 80, 80, 80);
  		Student s2 = new Student("张三", 80, 80, 80);
  		Student s3 = new Student("王五", 80, 80, 80);
  		stu.add(s1);
  		stu.add(s2);
  		stu.add(s3);
  		for(Student student : stu){
  			System.out.println(student);
  		}
  	}
  }
  ```

#### HashSet

- HashSet集合特点

  - 底层数据结构是哈希表
  - 不能保证存储和取出顺序完全一致
  - 没有带索引的方法，不能使用普通for循环遍历
  - 由于是Set集合，所以元素唯一

- 基本使用

  ```java
  import java.util.HashSet;
  import java.util.Iterator;
  
  //import java.util.TreeSet;
  
  public class Hash {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		HashSet<String> hs = new HashSet<>();
  		hs.add("hello");
  		hs.add("world");
  		hs.add("java");
  		hs.add("java");
  		hs.add("java");
  		hs.add("java");
  		
  		Iterator<String> it = hs.iterator();
  		while(it.hasNext()){
  			String s = it.next();
  			System.out.println(s);
  		}
  	}
  }
  ```

- 哈希值（哈希码值）：是JDK根据对象的**地址**或者**属性值**，算出来的int类型的**整数**
  - Object类中有一个方法可以获取**对象的哈希值**(`public int hashCode()`)
  - public int hashCode():根据对象的地址值计算出来的哈希值
- 对象的哈希值特点
  - 如果没有重写hashCode方法，那么是根据对象的地址值计算出的哈希值
  - 同一个对象多次调用hashCode()方法返回的哈希值是相同的
  - 不同对象的哈希值是不一样的
  - 如果重写了hasCode()方法，一般是通过对象的属性值计算出哈希值
  - 如果不同的对象属性值是一样的，那么计算出来的哈希值也是一样的

### Map&HashMap&TreeMap

#### Map

- Map集合概述和使用

  - Interface Map<K, V>       K:键的数据类型      V:值的数据类型
  - 键不能重复，值可以重复
  - 键和值是一一对应的，每一个键只能找到自己对应的值
  - （键+值）这个整体我们称之为“键值对” 或者“键值对对象”，在Java中叫做“Entry对象”
  - 双列集合一次可以存两个元素（一对数据）

- 创建Map集合的对象

  - 多态的方式

  - 具体的实现类HashMap

    ```java
    import java.util.HashMap;
    import java.util.Map;
    
    public class Base {
    
    	public static void main(String[] args) {
    		// TODO Auto-generated method stub
    		Map<String, String> stu = new HashMap<>();
    		stu.put("2020033001", "张三");
    		stu.put("2020033002", "李四");
    		stu.put("2020033003", "王五");
    		System.out.println(stu);
    	}
    }
    ```

- Map集合的基本功能

  |               方法名                |                 说明                 |
  | :---------------------------------: | :----------------------------------: |
  |        V put(K key, V value)        |               添加元素               |
  |        V remove(Object key)         |          根据键删除值对元素          |
  |            void clear()             |         移除所有的键值对元素         |
  |   boolean containsKey(Object key)   |       判断集合是否包含指定的键       |
  | boolean containsValue(Object value) |       判断集合是否包含指定的值       |
  |          boolean isEmpty()          |           判断集合是否为空           |
  |             int size()              | 集合的长度，也就是集合中键值对的个数 |

  > put方法中，如果要添加的键不存在，则会把键值对都添加到集合中；如果键存在，则会把原先的值覆盖，并当作返回值返回

- **遍历Map集合**

  - Map集合的获取功能

    |             方法名              |           说明           |
    | :-----------------------------: | :----------------------: |
    |         Set<K> keySet()         |     获取所有键的集合     |
    |        V get(Object key)        |       根据键获取值       |
    | Set<Map.Entry<K, V>> entrySet() | 获取所有键值对对象的集合 |
    |           K getKey()            |          获得键          |
    |          V getValue()           |          获得值          |

#### HashMap

- HashMap是Map里面的一个实现类。

- 没有额外需要学习的特有方法，直接使用Map里面的方法就可以了

- HashMap和HashSet的底层原理都是哈希表结构

- 依赖hashCode方法和equals方法保证**键**的唯一

- 如果**键**要存储的是自定义对象，需要重写hashCode和equals方法

- 案例
  需求：创建一个HashMap集合，键是学生对象（Student），值是籍贯（String）。存储三个键值对元素，并遍历

  ```java
  // Student类
  
  public class Student {
  	private String name;
  	private int age;
  	
  	public Student() {
  		super();
  	}
  
  	public Student(String name, int age) {
  		super();
  		this.name = name;
  		this.age = age;
  	}
  
  	public String getName() {
  		return name;
  	}
  
  	public void setName(String name) {
  		this.name = name;
  	}
  
  	public int getAge() {
  		return age;
  	}
  
  	public void setAge(int age) {
  		this.age = age;
  	}
  
  	@Override
  	public String toString() {
  		return "Student [name=" + name + ", age=" + age + "]";
  	}
  
  	@Override
  	public int hashCode() {
  		final int prime = 31;
  		int result = 1;
  		result = prime * result + age;
  		result = prime * result + ((name == null) ? 0 : name.hashCode());
  		return result;
  	}
  
  	@Override
  	public boolean equals(Object obj) {
  		if (this == obj)
  			return true;
  		if (obj == null)
  			return false;
  		if (getClass() != obj.getClass())
  			return false;
  		Student other = (Student) obj;
  		if (age != other.age)
  			return false;
  		if (name == null) {
  			if (other.name != null)
  				return false;
  		} else if (!name.equals(other.name))
  			return false;
  		return true;
  	}
  }
  ```

  ```java
  // 实现类
  
  import java.util.HashMap;
  import java.util.Set;
  import java.util.Map;
  
  public class HashDemo {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		HashMap<Student,String> hm = new HashMap<>();
  		Student s1 = new Student("张三",23);
  		Student s2 = new Student("李四",22);
  		Student s3 = new Student("王五",22);
  		hm.put(s1, "江苏");
  		hm.put(s2, "西安");
  		hm.put(s3, "北京");
  		
  		// 遍历方式一：获取所有的键，再找对应的值
  		Set<Student> keys = hm.keySet();
  		for(Student key : keys){
  			String value = hm.get(key);
  			System.out.println(key + "------" + value);
  		}
  		System.out.println("====================");
  		
  		// 遍历方式二：先获取到所有的键值对对象，再获取到里面的每一个键和值
  		Set<Map.Entry<Student, String>> entries = hm.entrySet();
  		for(Map.Entry<Student, String> entry: entries){
  			Student key = entry.getKey();
  			String value = entry.getValue();
  			System.out.println(key + "------" + value);
  		}
  		System.out.println("====================");
  		
  		// 遍历方式三：
  		hm.forEach(
  				(Student key, String value)->{
  					System.out.println(key + "-----" + value);
  				}
  		);
  	}
  }
  ```

#### TreeMap

- TreeMap是Map里面的一个实现类

- 没有额外需要学习的特有方法，直接使用Map里面的方法就可以了

- TreeMap和TreeSet一样，底层都是红黑树结构的

- 依赖自然排序或者比较器排序，对键进行排序

- 如果键存储的是自定义对象，需要实现Comparable接口或者在创建TreeMap对象时侯给出比较器排序规则

- 练习：创建一个TreeMap集合，键是学生对象（Student），值是籍贯（String）

  ​			学生属性姓名和年龄，按照年龄进行排序并遍历

  ```java
  // Student类
  public class Student implements Comparable<Student>{
  	private String name;
  	private int age;
  	
  	public Student() {
  		super();
  	}
  
  	public Student(String name, int age) {
  		super();
  		this.name = name;
  		this.age = age;
  	}
  
  	public String getName() {
  		return name;
  	}
  
  	public void setName(String name) {
  		this.name = name;
  	}
  
  	public int getAge() {
  		return age;
  	}
  
  	public void setAge(int age) {
  		this.age = age;
  	}
  
  	@Override
  	public String toString() {
  		return "Student [name=" + name + ", age=" + age + "]";
  	}
  
  	@Override
  	public int compareTo(Student o){
  		// 按照年龄进行排序
  		int result = this.getAge() - o.getAge();
  		// 次要条件，按照姓名排序
  		result = result == 0 ? this.getName().compareTo(o.getName()) : result;
  		return result;
      }
  }
  ```

  ```java
  // 实现类
  import java.util.TreeMap;
  public class TreeMapTest {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		TreeMap<Student, String> tm = new TreeMap<>();
  		
  		Student s1 = new Student("张三",23);
  		Student s2 = new Student("李四",22);
  		Student s3 = new Student("王五",22);
  		
  		tm.put(s1, "江苏");
  		tm.put(s2, "北京");
  		tm.put(s3, "天津");
  		
  		tm.forEach(
  				(Student key, String value)->{
  					System.out.println(key + "----" + value);
  				}
  		);
      }
  }
  ```

#### 可变参数

```java
// 需求：定义一个方法求N个数的和

// 在JDK5之前，会把所有的数据都先放到一个数组中，自定义方法形参只要写一个数组就可以了

public static void main(String[] args){
    int[] arr = {1, 2, 3, 4, 5};
    int sum1 = getSum(arr);
    System.out.println(sum1);
}
public static int getSum(int[] arr){
    int sum = 0;
    for(int i = 0; i < arr.length; i++){
        sum += arr[i];
    }
    return sum;
}
```

- 可变参数：就是形参的个数是可以变化的

- 格式：`修饰符 返回值类型 方法名(数据类型...变量名){ }`

- 注意事项：

  - 可变参数的底层其实就是一个数组
  - 如果一个方法有多个参数，包含可变参数，那么**可变参数要放在最后**

  ```java
  public static void main(String[] args){
      int sum = getSum(1, 2, 3, 4, 5, 6, 7);
      System.out.println(sum);
  }
  public static int getSum(int...arr){
      int sum = 0;
      for(int i = 0; i < arr.length; i++){
          sum += arr[i];
      }
      return sum;
  }
  ```

- 创建不可变集合

  - 在List、Set、Map接口中，都存在of方法，可以创建一个不可变的集合。
    这个集合不能添加、删除、修改

  |                  方法名                  |                说明                |
  | :--------------------------------------: | :--------------------------------: |
  |   static <E> List<E> of(E...elements)    | 创建一个具有指定元素的List集合对象 |
  |    static <E> Set<E> of(E...elements)    | 创建一个具有指定元素的Set集合对象  |
  | static <K, V> Map<K, V> of(E...elements) | 创建一个具有指定元素的Map集合对象  |

  - 应用场景
    - 集合元素的批量添加：`ArrayList<String> list = new ArrayList<>(List.of("a", "b", "c", "d"));`

### Stream流

#### Stream流的三类方法

- 获取Stream流
  创建一条流水线，并把数据放到流水线上准备进行操作
- 中间方法
  流水线上的操作
  一次操作完毕之后，还可以继续进行其他操作
- 终结方法
  一个Stream流只能有一个终结方法
  是流水线上的最后一个方法

#### Stream流的获取方法

- 单列集合
  可以使用Collection接口中的默认方法stream()生成流:`集合对象.stream();`
  `default Stream<E> stream()`
- 双列集合
  **间接**的生成流
  可以先通过keySet或者entrySet获取一个Set集合，再获取Stream流:`集合对象.keySet().stream();` `集合对象.entrySet().stream();`
- 数组
  Arrays中的静态方法stream生成流：`Arrays.stream(数组名);`
- 同种数据类型的多个数据
  1, 2, 3, 4, 5, 6...
  "aaa", "bbb", "ccc", ...
  使用Stream.of(T...values)生成流

#### 中间方法

- Stream<T> filter(Predicate predicate):用于对流中的数据进行**过滤**
  Predicate接口中的方法
  boolean test(T t)：对给定的参数进行判断，返回一个布尔值
- Stream<T> limit(long maxSize)：**截取**指定参数个数的数据
- Stream<T> skip(long n)：**跳过**指定参数个数的数据
- static <T> Stream<T> concat(Stream a, Stream b)：**合并**a和b两个流为一个流
- Stream<T> distinct()：**去**除流中**重**复的元素，底层依赖(hashCode和equals方法)

#### 终结方法

- void forEach(Consumer action):对此流的每个元素执行操作
  Consumer接口中的方法		void accept(T t):对给定的参数执行此操作
- long count():返回此流中的元素数

**在Stream流中无法直接修改集合，数组等数据源中的数据**

#### 收集方法

- R collect(Collector collector)
- 工具类Collectors提供了具体的收集方式
  - public static <T> Collector toList():把元素收集到List集合中
  - public static <T> Collector toSet()：把元素收集到Set集合中
  - public static Collector toMap(Function keyMapper, Function valueMapper)：把元素收集到Map集合中
- collect方法只能获取到流中剩余的每一个数据，在底层不能创建容器，也不能把数据添加到容器中，需要用Collectors

#### 练习

- 现在又两个ArrayList集合，分别存储6名男演员和6名女演员，要求完成以下操作
  - 男演员只要名字为3个字的前两人
  - 女演员只要姓杨的，并且不要第一个
  - 把过滤后的男演员和女演员姓名合并到一起
  - 把上一步操作后的元素作为构造方法的参数创建演员对象，遍历数据

```java
package Stream;

import java.util.ArrayList;
import java.util.stream.Stream;

public class Demo{
    public static void main(String[] args){
        ArrayList<String> manList = new ArrayList<>();
        manList.add("张国立");
        manList.add("张晋");
        manList.add("刘烨");
        manList.add("郑尹健");
        manList.add("徐峥");
        manList.add("王宝强");
        ArrayList<String> womanList = new ArrayList<>();
        womanList.add("郑爽");
        womanList.add("杨紫");
        womanList.add("关晓彤");
        womanList.add("张天爱");
        womanList.add("杨幂");
        womanList.add("赵丽颖");
        
        Stream<String> stream1 = manList.stream().filter(name -> name.length() == 3).limit(2);
        
        Stream<String> stream2 = womanList.stream().filter(name -> name.startsWith("杨")).skip(1);
        
        Stream.concat(stream1, stream2).forEach(name -> System.out.println(name));;
    }
}
```



## IO流

### File

#### 概述

- IO就可以对硬盘中的文件进行读写
- File表示要读写的文件在哪，也可以对文件进行创建，删除等操作
- IO流是什么
  - 可以将数据从本地文件中读取出来
  - 可以将数据从内存保存到本地文件
- File类是什么
  - 在读写数据时告诉虚拟机要操作的文件/文件夹在哪
  - 对文件/文件夹本身进行操作，包括创建、删除等

#### File

File:它是文件和目录路径名的抽象表示

- 文件和目录可以通过File封装成对象
- File封装的对象仅仅是一个路径名。它可以是存在的，也可以是不存在的

#### 构造方法

|              方法名               |                             说明                             |
| :-------------------------------: | :----------------------------------------------------------: |
|       File(String pathname)       |  通过将给定的路径名字符串转换为抽象路径名来创建新的File实例  |
| File(String parent, String child) | 从父路径名字符串和子路径名字符串创建新的File实例（路径拼接） |
|  File(File parent, String child)  |  从父抽象路径名和子路径名字符串创建新的File实例（路径拼接）  |

> Q：为什么要把字符串表示形式的路径变为File对象？
>
> A：就是为了使用File类里面的方法

#### 绝对路径和相对路径

- 绝对路径：从盘符开始（完整的路径）
- 相对路径：相对当前项目下的路径

#### 相应操作

- File类创建功能

  | 方法名                         | 说明                       |
  | ------------------------------ | -------------------------- |
  | public boolean createNewFile() | 创建一个新的空的文件       |
  | public boolean mkdir()         | 创建一个单级文件夹（了解） |
  | public boolean mkdirs()        | 创建一个多级文件夹         |

  > createNewFile			只能创建文件；   如果文件存在，创建失败，返回false；    如果文件不存在，创建文件，返回true；     要求文件所在文件夹必须存在
  >
  > mkdir				只能创建单级文件夹；     只能创建文件夹；
  >
  > mkdirs 				可以创建单击文件夹，也可以创建多级文件夹
  >
  > 创建文件夹的方法，mkdir只需要了解，掌握mkdirs即可

- File类删除功能：`public boolean delete()`       删除由此抽象路径名表示的文件或目录

  > 删除后不进回收站，不能恢复；     可以删除文件，也可以删除文件夹；			如果删除的是文件，直接删除；如果删除的是文件夹，只能删除空文件夹

- File类判断和获取功能

  |            方法名            |                   说明                   |
  | :--------------------------: | :--------------------------------------: |
  | public boolean isDirectory() |   测试此抽象路径名表示的File是否为目录   |
  |   public boolean isFile()    |   测试此抽象路径名表示的File是否为文件   |
  |   public boolean exists()    |    测试此抽象路径名表示的File是否存在    |
  |   public String getName()    | 返回由此抽象路径名表示的文件或目录的名称 |

  > getName方法：如果调用者是文件，那么获取的是文件名和后缀名；如果调用者是文件夹，那么获取的是文件夹的名字

- File类高级获取功能：`public File[] listFiles()`：返回此抽象路径名表示的目录中的文件和目录的File对象数组

  - 进入文件夹，获取这个文件夹里面所有的文件和文件夹的File对象，并把这些File对象都放在一个数组中返回
  - 包括隐藏文件和隐藏文件夹，都可以获取出来

  > 当调用者是一个文件或不存在时，会返回一个null
  >
  > 当调用者是一个空文件夹时，会返回一个长度为0的数组
  >
  > 当调用者是一个有权限才能进入的文件夹时，会返回一个null

#### 练习

- 练习一：在当前模块下的aaa文件夹中创建一个a.txt文件

  ```java
  import java.io.File;
  import java.io.IOException;
  
  public class Demo1{
      public static void main(String[] args) throws IOException{
          File file = new File("File\\aaa");
          if(!file.exists()){		// 如果文件夹不存在，创建文件夹
              file.mkdirs();
          }
          File newFile = new File(file, "a.txt");
          newFile.createNewFile();		// 要保证文件所在的文件夹必须存在
      }
  }
  ```

- 练习二：删除一个多级文件夹

  ```java
  import java.io.File;
  
  public class Demo2{
      public static void main(String[] args){
          File src = new File("C:\\Users\\lihao\\Desktop\\cs");
          deleteDir(src);
      }
      
      private static void deleteDir(File src){
          // 递归思路
          // 套路：
          // 1.进入----得到src文件夹里面所有内容的File对象
          File[] files = src.listFiles();
          // 2.遍历----得到src文件夹里面每一个文件和文件夹的File对象
          for(File file:files){
              // 3.判断----如果遍历到的File对象是一个文件就直接删除
              if(file.isFile()){
                  file.delete();
              }else{		// 4.判断----如果遍历到的File对象是一个文件夹,递归
                  deleteDir(file); 			// 参数一定要是src文件夹里面的文件夹File对象
              }
          }
          src.delete();
      }
  }
  ```

- 练习三：统计一个文件夹中每种文件的个数并打印
  				打印格式如下：
        												txt:3个
        												doc:4个
        												..........

  ```java
  public class Demo3{
      public static void main(String[] args){
          File file = new file("File");
          HashMap<String, Integer> hm = new HashMap<>();
          getCount(hm, file);
          System.out.println(h)
      }
      
      private static void getCount(HashMap<String, Integer> hm, File file){
          File[] files = file.listFiles();
          for(File f:files){
              if(f.isFile()){
                  String fileName = f.getName();
                  String[] fileNameArr = fileName.split("\\.");
                  if(fileNameArr.length == 2){
                      String fileEndName = fileNameArr[1];
                      if(hm.containsKey(fileEndName)){
                          // 已经存在
                          // 将已经出现的次数获取出来
                          Integer count = hm.get(fileEndName);
                          // 该文件再次出现
                          count++;
                          hm.put(fileEndName, count);
                      }else{
                          // 不存在
                          // 当前文件是第一次出现
                          hm.put(fileEndName, 1);
                      }
                  }
              }else{
                  getCount(hm, f);
              }
          }
      }
  }
  ```


### 字节流

#### IO流的概述和分类

- 其中，I表示input，是数据从硬盘进内存的过程，称之为读
  			O表示output，是数据从内存到硬盘的过程，称之为写
- IO的数据传输，可以看作是一种数据的流动，按照流动的方向，以内存为参照物，进行读写操作
  简单来说：**内存在读，内存在写**
- 按流向分：输入流、输出流
- 按数据类型分：字节流、字符流
  字节流：操作所有类型的文件（包括音频、视频、图片等）
  字符流：只能操作纯文本文件（包括Java文件、txt文件等）
  一般来说，我们说的IO流的分类是按照**数据类型**来分的
  纯文本文件：用windows自带的记事本打开能读得懂的文件
- IO流的技术选型

#### 字节流写数据

- 步骤

  - 创建字节输出流对象(`FileOutputStream fos = new FileOutputStream("a.txt")  `)
  - 写数据(`fos.write(数据)`)
  - 释放资源(`fos.close();`)

- 注意点

  - 如果文件不存在，会自动创建出来；如果文件存在，会把文件清空
  - 给write方法传递一个整数时，写入的数据是这个整数在ASCII码表中对应的字符
  - 释放资源指令，表示告诉操作系统，已经不再使用这个文件了。**每次使用完流必须要释放资源**

- 字节流写数据的3种方式

  | 方法名                                 | 说明                         |
  | -------------------------------------- | ---------------------------- |
  | void write(int b)                      | 一次写一个数据               |
  | void write(byte[] b)                   | 一次写一个字节数组数据       |
  | void write(byte[] b, int off, int len) | 一次写一个字节数组的部分数据 |

- 两个小问题

  - 字节流写完数据如何实现换行
    写完数据后，加换行符：`\r`   `\n`   `getBytes()`

  - 字节流写数据如何实现追加写入呢(保留原数据)？

    在`public FileOutputStream(String name, boolean append)`				true表示续写开关，保留原数据；默认为false

#### 捕获异常

```java
try{
    FileOutputStream fos = new FileOutputStream("a.txt");
    fos.write(97);
    fos.close();
}catch (IOException e){
    e.printStackTrace();
}
```

> 上述方法在`fos.write(97);`出异常后，close方法将无法执行。那么如何操作才能让close方法一定执行呢？

- finally:在异常处理时提供finally块来执行所有清除操作。比如说IO流中的释放资源

  - 特点：被finally控制的语句一定会执行，除非JVM退出

  - 异常处理标准格式：`try...catch...finally`

    ```java
    FileOutputStream fos = null;
    try{
        fos = new FileOutputStream("a.txt");
        fos.write(97);
    }catch (IOException e){
        e.printStackTrace();
    }finally{
        //finally 中的代码一定会执行
        if(fos != null){
            try{
            	fos.close();
        	}catch(IOException e){
            	e.printStackTrace();
        	}
        }
    }
    ```

#### 字节流读数据

- 步骤

  - 创建字节输入流对象(`FileInputStream fis = new FileInputStream("a.txt");`)
    - 如果文件存在，不会报错；如果文件不存在，那么直接报错
  - 读数据(`int read = fis.read();`)
    - 一次读取一个字节，返回值就是本次读到的那个字节数据
    - 也就是字符在码表中对应的那个数字
    - 如果想要看到的是字符数据，一定要强转成char
  - 释放资源(`fis.close();`)

- 读取多个字节数据

  - 当读取到文件结束时，会返回-1

    ```java
    int b;
    while((b = fis.read()) != -1){
        System.out.println((char)b);
    }
    fis.close();
    ```

#### 复制文件案例

- 需求：把"E:\\\study\\\a.txt" 复制到当前模块下

  - 复制文件，其实就是把文件中的内容从一个文件中读取出来(**数据源**)，然后写入到另一个文件中(**目的地**)

  ```java
  import java.io.FileInputStream;
  import java.io.FileNotFoundException;
  import java.io.FileOutputStream;
  import java.io.IOException;
  
  public class Demo2 {
  
  	public static void main(String[] args) throws IOException {
  		// TODO Auto-generated method stub
  		FileInputStream fis = new FileInputStream("E:\\study\\test.txt");
  		FileOutputStream fos = new FileOutputStream("test.txt");
  		int b;
  		while((b = fis.read()) != -1){
  			fos.write(b);
  		}
  		fis.close();
  		fos.close();
  	}
  }
  ```

#### 定义小数组拷贝

- 如果操作的文件过大，那么速度就会很**慢**

- 为了解决速度问题，字节流通过创建字节数组，可以一次读写多个数据

- 一次读一个字节数组的方法：

  - `public int read(byte[] b)`：从输入流读取最多b.length个字节的数据
  - 返回的是读入缓冲区的总字节数，也就是实际的读取字节个数

  ```java
  import java.io.FileInputStream;
  import java.io.FileNotFoundException;
  import java.io.FileOutputStream;
  import java.io.IOException;
  
  public class Demo3 {
  
  	public static void main(String[] args) throws IOException {
  		// TODO Auto-generated method stub
  		FileOutputStream fos = new FileOutputStream("a.test");
  		FileInputStream fis = new FileInputStream("E:\\study\\test.txt");
  		byte[] bytes = new byte[1024];
  		int len;		// 本次读取到的有效字节个数-----这次读了几个字节
  		while((len = fis.read(bytes)) != -1){
  			fos.write(bytes, 0, len);
  		}
  		fis.close();
  		fos.close();
  	}
  }
  ```

### 缓冲流

- 字节缓冲流：提高读和写的效率
  - BufferedOutputStream：字节缓冲输出流
  - BufferedInputStream：字节缓冲输入流

#### 构造方法

- 字节缓冲输出流：`BufferedOutputStream(OutputStream out)`

- 字节缓冲输入流：`BufferedInputStream(InputStream in)`

- 字节缓冲流**仅仅提供缓冲区**（数组），而真正的读写数据还得依靠基本的字节流对象进行操作

  ```java
  import java.io.*;
  
  public class Demo1 {
  
  	public static void main(String[] args) throws IOException {
  		// TODO Auto-generated method stub
  		// 创建字节缓冲输入流
          // 在底层创建了一个默认长度为8192的字节数组
  		BufferedInputStream bis = new BufferedInputStream(new FileInputStream("E:\\study\\test.txt"));
  		// 创建字节缓冲输出流
  		BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("test.txt"));
  		
  		int b;
  		while((b = bis.read()) != -1){
  			bos.write(b);
  		}
          // f
  		bis.close();
  		bos.close();
  	}
  }
  ```

  

### 字符流&字符缓冲流

#### 编码表

- 基础知识

  - 计算机中储存的信息都是用**二进制**数表示的
  - 按照某种规则，将字符变成二进制，再存储到计算机中，称为**编码**
  - 按照同样的规则，将存储在计算机中的二进制数解析显示出来，称为**解码**
  - 编码和解码的方式必须要一致，否则会导致乱码

- ASCII字符集

  - **ASCII**（美国信息交换标准代码）：包括了数字，大小写字符和一些常见的标点符号。
    注意：ASCII码表中是没有中文的

- GBK：==windows系统默认的码表==。兼容ASCII码表，也包含了21003个汉字，并支持繁体汉字以及部分日韩文字。
  注意：GBK是中国的码表，一个中文以**两个字节**的形式存储。但不包含世界上所有国家的文字。

- Unicode码表：由国际组织ISO制定，是统一的万国码，计算机科学领域里的一项业界标准，容纳世界上大多数国家的所有常见文字和符号

  但是因为表示的字符太多，所有Unicode码表中的数字不是直接以二进制的形式存储到计算机的
  会先通过UTF-7,UTF-7.5,UTF-8,UTF-16,以及UTF-32进行编码，再存储到计算机，其中最常见的就是UTF-8
  注意：Unicode是万国码，以UTF-8编码后一个中文以**三个字节**的形式存储

- 重点：Windows默认使用码表为**GBK**，一个字符**两**个字节
  idea和以后工作默认使用Unicode的**UTF-8**编解码格式，一个中文**三**个字节

#### 字符串中的编码解码问题

- 编码
  - `byte[] getBytes()`：使用平台默认字符集将该String编码为一系列字节，将结果存储到新的字节数组中
  - `byte[] getBytes(String charsetName)`：使用指定的字符集将该String编码为一系列字节，将结果存储到新的字节数组中
- 解码
  - `String(byte[] bytes)`：通过使用平台的默认字符集解码指定的字节数组来构造新的String
  - `String(bytes,String charsetName)`：通过指定的字符集解码指定的字节数组来构造新的String

```java
import java.io.UnsupportedEncodingException;
import java.util.Arrays;

public class Demo1 {

	public static void main(String[] args) throws UnsupportedEncodingException {
		// TODO Auto-generated method stub
		String s = "好好学习，天天向上";
		// 利用默认的GBK将中文编码为一系列的字节
		byte[] bytes1 = s.getBytes();
		System.out.println(Arrays.toString(bytes1));
		// 指定为UTF-8编码格式
		byte[] bytes2 = s.getBytes("UTF-8");
		System.out.println(Arrays.toString(bytes2));
		byte[] bytes3 = {-70, -61, -70, -61, -47, -89, -49, -80, -93, -84, -52, -20, -52, -20, -49, -14, -55, -49};
		byte[] bytes4 = {-27, -91, -67, -27, -91, -67, -27, -83, -90, -28, -71, -96, -17, -68, -116, -27, -92, -87, -27, -92, -87, -27, -112, -111, -28, -72, -118};
		String s1 = new String(bytes3);
		String s2 = new String(bytes4,"UTF-8");
		System.out.println(s1);
		System.out.println(s2);
	}
}
```

- 为什么字节流读取文本文件，可能出现乱码
  因为字节流一次读一个字节，而不管GBK还是UTF-8一个中文都是多个字节，用字节流每次只能读其中的一部分，所有就会出现乱码问题

#### 字符流读取中文的过程

- **字符流 = 字节流 + 编码表**
- 基础知识
  - 不管是在哪张码表中，中文的第一个字节一定是负数
- 想要进行拷贝，一律使用字节流或者字节缓冲流
  想要把文本文件中的数据**读到**内存中，请使用字符输入流
  想要把内存中的数据**写到**文本文件中，请使用字符输出流
- GBK码表一个中文两个字节，UTF-8编码格式一个中文三个字节

#### 写出数据

- 步骤

  - 创建字符输出流对象
    - 如果文件不存在，就创建。但要保证父级路径存在
    - 如果文件存在就清空
  - 写数据
    - 如果写出int类型的整数，实际写出的是整数在码表中对应的字母（如果要写整数，用字符串写）
    - 写出字符串数据，是把字符串本身原样写出
  - 释放资源（每次操作完最后必须释放资源）

- 字符流写数据的5种方式

  |                  方法名                   |         说明         |
  | :---------------------------------------: | :------------------: |
  |             void write(int c)             |      写一个字符      |
  |          void write(char[] cbuf)          |   写出一个字符数组   |
  | void write(char[] cbuf, int off, int len) | 写出字符数组的一部分 |
  |          void write(String str)           |     写一个字符串     |
  | void write(String str, int off, int len)  | 写一个字符串的一部分 |

  ```java
  import java.io.FileWriter;
  import java.io.IOException;
  
  public class Demo2 {
  
  	public static void main(String[] args) throws IOException {
  		// TODO Auto-generated method stub
  		
  		
  		// 创建字符输出流对象
  		FileWriter fw = new FileWriter("src\\CharStream\\a.txt");
  		// FileWriter fw = new FileWriter(new File("CharStream\\a.txt"));
  		
  		
  		// 写出数据(一次一个字符)
  		// method1(fw);
  		
  		// 写一个字符数组
  		// method2(fw);
  		
  		// 写出字符数组的一部分
  		// method3(fw);
  		
  		// 写出一个字符串[重点]
  		// method4(fw);
  		
  		// 写出一个字符串的一部分（了解）
  		// method5(fw);
  		
  		// 释放资源
  		fw.close();
  		
  		
  	}
  
  	private static void method5(FileWriter fw) throws IOException {
  		fw.write("好好学习，天天向上", 3, 4);
  	}
  
  	private static void method4(FileWriter fw) throws IOException {
  		String line = "好好学习,";
  		fw.write(line);
  		fw.write("天天向上");
  	}
  
  	private static void method3(FileWriter fw) throws IOException {
  		char[] chars = {97, 98, 99, 100, 101, 102, 103};
  		fw.write(chars, 3, 4);
  	}
  
  	private static void method2(FileWriter fw) throws IOException {
  		char[] chars = {97, 98 ,99, 100, 101};
  		fw.write(chars);
  	}
  
  	private static void method1(FileWriter fw) throws IOException {
  		fw.write(97);
  		fw.write(98);
  		fw.write(99);
  	}
  }
  ```

#### flush和close方法

| 方法名  | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| flush() | 刷新流，还可以继续写数据                                     |
| close() | 关闭流，释放资源，但是在关闭之前会先刷新流。一旦关闭，就不能再写数据 |

- 在写数据后，必须执行刷新流才能将内容最终写入文件种(close会在关闭流前刷新流)

#### 字符流读数据的过程

- 步骤

  - 创建字符输入流对象：`FileReader fr = new FileReader("a.txt");` `FileReader fr = new FileReader(new File("a.txt"));`
  - 读取数据：`fr.read();`
  - 释放资源：`fr.close();`

- 一次读取多个字符

  ```java
  import java.io.FileReader;
  import java.io.IOException;
  
  public class Demo3 {
  	public static void main(String[] args) throws IOException{
  		// 创建对象
  		FileReader fr = new FileReader("src\\CharStream\\a.txt");
  		
  		// 创建数组
  		char[] chars = new char[1024];
  		int len;
  		while((len = fr.read(chars)) != -1){
  			System.out.println(new String(chars, 0, len));
  		}
  		
  		// 释放资源
  		fr.close();
  	}
  }
  ```

#### 练习

- 保存键盘录入的数据
  - 需求：将用户键盘录入的用户名和密码保存到本地实现永久化存储。
    			要求用户名独占一行，密码独占一行。

```java
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class Demo4 {
	public static void main(String[] args) throws IOException{
		Scanner sc = new Scanner(System.in);
		System.out.println("【用户注册】");
		System.out.print("请输入用户名(6位)：");
		String userName = sc.next();
		System.out.print("请输入密码(6位)：");
		String passWord = sc.next();
		FileWriter fw = new FileWriter("user.txt");
		fw.write(userName + "\n" + passWord);
		fw.close();
		System.out.println("注册成功！");
		System.out.println("【用户登录】");
		System.out.print("请输入用户名：");
		String user = sc.next();
		System.out.print("请输入密码：");
		String pass = sc.next();
		FileReader fr = new FileReader("user.txt");
		char[] chars = new char[1024];
		int len;
		while((len = fr.read(chars)) != -1){
			userName = new String(chars, 0, 6);
			passWord = new String(chars, 7 , 6);
		}
		if(user.equals(userName) && pass.equals(passWord)){
			System.out.println("登录成功！");
		}else{
			System.out.println("密码错误，登录失败！");
		}
	}
}
```

#### 字符缓冲流

- BufferedWriter(字符缓冲输出流)：可以将数据高效的写出
- BufferedReader(字符缓冲输入流)：可以将数据高效的读取到内存
- **需要传入FileWriter或者FileReader对象，不能直接传入字符串地址或者File对象**
- 字符缓冲流特有方法
  - BufferedWriter
    - `void newLine()`：写一行行分隔符，行分隔符字符串由系统属性定义（回车换行）
  - BufferedReader
    - `public String readLine()`：读一行文字。结果包含行内的内容的字符串，不包括任何行终止字符，如果流的结尾已经到达，则为null

#### 练习

- 需求：读取文件中的数据，排序后再次写到本地文件

  ```java
  import java.io.BufferedReader;
  import java.io.BufferedWriter;
  import java.io.FileReader;
  import java.io.FileWriter;
  import java.io.IOException;
  import java.util.Arrays;
  public class Demo5 {
  	public static void main(String[] args) throws IOException{
  		// 创建字符缓冲输入流对象
  		BufferedReader br = new BufferedReader(new FileReader("sort.txt"));
  		String s = br.readLine();		// 8 7 5 2 1 3 4 9 10 6
  		String[] n = s.split(" ");
  		int[] num = new int[n.length];
  		for(int i = 0; i < n.length; i++){
  			int number = Integer.parseInt(n[i]);
  			num[i] = number;
  		}
  		Arrays.sort(num);
  		br.close();
  		// 写入
  		BufferedWriter bw = new BufferedWriter(new FileWriter("sort.txt"));
  		for(int i = 0; i < num.length; i++){
  			bw.write(num[i] + " ");
  			bw.flush();
  		}
  		bw.close();
  	}
  }
  ```

#### 小结

- 字节流用来拷贝文件
- 字符流用来进行文件的读写
- 缓冲流用来提高效率

### 转换流&对象操作流&Properties

#### 转换流

- 输入流：InputStreamReader，字节流到字符流的桥梁，把字节流转换为字符流
- 输出流：OutputStreamWriter，字符流到字节流的桥梁，把字符流转换为字节流
- 使用场景
  - 在JDK11以前，可用于指定编码读写`InputStreamReader("a.txt","utf-8");`
  - 在JDK11之后，字符流新推出了一个构造，也可以指定编码表
    `FileReader fr = new FileReader("a.txt",charset.forName("UTF-8"));`

#### 对象操作流

- 特点：可以把对象以字节的形式写到本地文件，直接打开文件，是读不懂的，需要再次用对象操作流读到内存中

- 对象操作流分为两类

  - 对象操作输出流(对象序列化流)：ObjectOutputStream，就是将对象写到本地文件中，或者在网络中传输对象

  - 对象操作输入流(对象反序列化流)：ObjectInputStream，把写到本地文件中的对象读到内存中，或者接收网络中传输的对象


```java
// User类
package Streamio;

import java.io.Serializable;

//	如果想要这个类的对象能被序列化，那么这个类就必须实现一个接口
public class User implements Serializable{
	
	//	成员变量
	private String userName;
	private String passWord;
	
	//	构造方法
	public User() {
		super();
	}
	public User(String userName, String passWord) {
		super();
		this.userName = userName;
		this.passWord = passWord;
	}
	//	成员方法
	public String getUserName() {
		return userName;
	}
	public void setUserName(String userName) {
		this.userName = userName;
	}
	public String getPassWord() {
		return passWord;
	}
	public void setPassWord(String passWord) {
		this.passWord = passWord;
	}
	@Override
	public String toString() {
		return "User [userName=" + userName + ", passWord=" + passWord + "]";
	}	
}
```

> Serializable接口的意义：标记性接口，里面没有任何抽象方法，只要一个类实现类这个Serializable接口，那么就表示这个类的对象可以被序列化

```java
// 实现类	对象操作输出流
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

public class Demo1 {
	public static void main(String[] args) throws FileNotFoundException, IOException {
		User user = new User("zhangsan","qwer");
		// 需求：把这个用户信息保存到本地文件
		ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("a.txt"));
		oos.writeObject(user);
		oos.close();
	}
}
```

```java
// 实现类  写：对象操作输入流
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.ObjectInputStream;

public class Demo2 {
	public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException {
		// TODO Auto-generated method stub
		ObjectInputStream ois = new ObjectInputStream(new FileInputStream("a.txt"));
		User o = (User) ois.readObject();
		System.out.println(o);
		ois.close();
	}
}
```

#### 注意点

- 用对象序列化流序列化了一个对象后，假如我们修改了对象所属的Javabean类（对象实现类），读取数据会不会出问题？
  - serialVersionUID序列号：如果没有手动定义，虚拟机会根据类中的信息自动计算出一个序列号
  - 如果我们修改了类中的信息，虚拟机会再次计算出一个序列号
- 如果出问题了，如何解决？
  - 不让虚拟机计算序列号，自己手动给出一个不变的序列号
    `private static final long serialVersionUID = 1L;`
    1L可以自定义，只要不超出long的范围即可
- 如果一个对象中的某个成员变量的值不想被序列化，又该如何实现？
  使用关键字`transient`修饰，该关键字标记的成员变量不参与序列化过程

#### 练习

- 案例：用对象操作流读写多个对象

  ```java
  // 需求：创建多个JavaBean类对象写到文件中，再次读取到内存
  // Student类
  import java.io.Serializable;
  
  public class Student implements Serializable{
  	private String name;
  	private int age;
  	private static final long serialVersionUID = 1L;
  	public Student() {
  		super();
  	}
  	public Student(String name, int age) {
  		super();
  		this.name = name;
  		this.age = age;
  	}
  	public String getName() {
  		return name;
  	}
  	public void setName(String name) {
  		this.name = name;
  	}
  	public int getAge() {
  		return age;
  	}
  	public void setAge(int age) {
  		this.age = age;
  	}
  	@Override
  	public String toString() {
  		return "Student [name=" + name + ", age=" + age + "]";
  	}	
  }
  ```

  ```java
  // 实现类
  import java.io.FileInputStream;
  import java.io.FileNotFoundException;
  import java.io.FileOutputStream;
  import java.io.IOException;
  import java.io.ObjectInputStream;
  import java.io.ObjectOutputStream;
  
  public class Demo3 {
  	public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException{
  		Student s1 = new Student("张三",23);
  		Student s2 = new Student("李四",24);
  		Student s3 = new Student("王五",25);
  		// 写入
  		ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("b.txt"));
  		oos.writeObject(s1);
  		oos.writeObject(s2);
  		oos.writeObject(s3);
  		oos.close();
  		// 读出
  		ObjectInputStream ois = new ObjectInputStream(new FileInputStream("b.txt"));
  		while(true){
  			try{
  				Student stu = (Student) ois.readObject();
  				System.out.println(stu);
  			} catch(IOException e){
  				break;
  			}
  		}
  		ois.close();
  	}
  }
  ```

#### Properties

- 概述

  - 是一个Map体系的集合类
  - Properties中有跟IO相关的方法
  - 键值对的数据类型基本都定义为字符串

- 练习：Properties作为Map集合的使用

  ```java
  package Properties;
  
  import java.util.Map.Entry;
  import java.util.Properties;
  import java.util.Set;
  
  public class Demo1 {
  
  	public static void main(String[] args) {
  		// TODO Auto-generated method stub
  		Properties prop = new Properties();
  		// 增
  		prop.put("唐三", "小舞");
  		prop.put("戴沐白", "朱竹青");
  		prop.put("奥斯卡", "宁荣荣");
  		// 删
  		prop.remove("戴沐白");
  		// 改
  		prop.put("奥斯卡", "朱竹青");
  		// 查
  		Object value = prop.get("唐三");
  		// 遍历
  		Set<Object> keys = prop.keySet();
  		for(Object key : keys){		// 所有的键
  			Object r = prop.get(key);
  			System.out.println(key + "=" + r);
  		}
  		// 所有的键值对对象
  		Set<Entry<Object, Object>> entries = prop.entrySet();
  		for(Entry<Object, Object> entry :entries){
  			Object key = entry.getKey();
  			Object val = entry.getValue();
  			System.out.println(key + "---" + val);
  		}
  	}
  }
  ```

- 作为集合的特有方法

  |                    方法名                    |                             说明                             |
  | :------------------------------------------: | :----------------------------------------------------------: |
  | Object setProperty(String key, String value) |   设置集合的键和值，都是String类型，底层调用Hashtable方法    |
  |        String getProperty(String key)        |               使用此属性列表中指定的键搜索属性               |
  |      Set<String> stringPropertyNames()       | 从该属性列表中返回一个不可修改的键集，其中键及其对应的值是字符串 |

- Properties和IO流结合的方法

  |                    方法名                     |                             说明                             |
  | :-------------------------------------------: | :----------------------------------------------------------: |
  |        void load(InputStream inStream)        |             从输入字节流读取属性列表(键和元素对)             |
  |          `void load(Reader reader)`           |             从输入字符流读取属性列表(键和元素对)             |
  | void store(OutputStream out, String comments) | 将此属性列表(键和元素对)写入此Properties表中，以适合于使用load(InputStream)方法的格式写入输出字节流 |
  | `void store(Writer writer, String comments)`  | 将此属性列表(键和元素对)写入此Properties表中，以适合使用load(Reader)方法的格式写入输出字符流 |

  ```java
  // 读取
  import java.io.FileReader;
  import java.io.IOException;
  import java.util.Properties;
  
  public class Demo2 {
  
  	public static void main(String[] args) throws IOException {
  		// TODO Auto-generated method stub
  		Properties prop = new Properties();
  		FileReader fr = new FileReader("src\\Properties\\prop.properties");
  		// 调用完了load方法之后，文件中的键值对数据已经在集合中了
  		prop.load(fr);
  		fr.close();
  		System.out.println(prop);
  	}
  }
  ```

  ```java
  // 保存
  import java.io.FileWriter;
  import java.io.IOException;
  import java.util.Properties;
  
  public class Demo3 {
  
  	public static void main(String[] args) throws IOException {
  		// TODO Auto-generated method stub
  		Properties prop = new Properties();
  		prop.put("zhangsan", "123");
  		prop.put("lisi", "456");
  		prop.put("wangwu", "789");
  		FileWriter fw = new FileWriter("src\\Properties\\prop.properties");
  		prop.store(fw, "注释");		// 注释不填可以填写null
  		fw.close();
  	}
  }
  ```

  

## 多线程

### 多线程

- 多线程是指从软件或者硬件上实现多个线程并发执行的技术
- 具有多线程能力的计算机因有硬件支持而能够在同一时间执行多个线程，提升性能

#### 并发和并行

- 并行：在同一时刻，有多个指令在==多个==CPU上==同时==执行
- 并发：在同一时刻，有多个指令在==单个==CPU上==交替==执行

#### 进程和线程

- 进程：就是操作系统中正在运行的一个应用程序
  - 独立性：进程是一个能独立运行的基本单位，同时也是系统分配资源和调度的独立单位
  - 动态性：进程的实质是程序的一次执行过程，进程是动态产生，动态消亡的
  - 并发性：任何进程都可以和其他进程一起并发执行
- 线程：是进程中的单个顺序控制流，是一条执行路径
  - 单线程：一个进程如果只有一条执行路径，则称为单线程程序
  - 多线程：一个进程如果有多条执行语句，则称为多线程程序

#### 实现方式

- 继承Thread类的方式进行实现

  - 定义一个MyThread继承Thread类

  - 在MyThread类中重写run()方法

  - 创建MyThread类的对象

  - 启动线程

    ```java
    // MyThread类
    public class MyThread extends Thread{
        @Override
        public void run{
            // 代码就是线程在开启之后执行的代码
            for(int i = 0; i < 100; i++){
                System.out.println("线程开启了" + i);
            }
        }
    }
    ```

    ```java
    // 测试类
    public class Demo{
        public static void main(String[] args){
            // 创建两个线程对象
            MyThread t1 = new MyThread();
            MyThread t2 = new MyThread();
            // 开启一条线程
            t1.start();
            // 开启第二条线程
            t2.start();
        }
    }
    ```

    >多线程程序，线程交替进行执行，是随机的，所以每次执行的结果可能都不一样
    >
    >- 两个小问题
    >
    >  - 为什么要重写run()方法?
    >    因为run()是用来封装被线程执行的代码
    >
    >  - run()方法和start()方法的区别？
    >    run()：封装线程执行的代码，直接调用，相当于普遍方法的调用，并没有开启线程
    >
    >    start()：启动线程，然后由JVM调用此线程的run()方法

- 实现Runnable接口的方式进行实现

  - 定义一个类MyRunnable实现Runnable接口

  - 在MyRunnable类中重写run()方法

  - 创建MyRunnable类的对象

  - 创建Thread类的对象，把MyRunnable对象作为构造方法的参数

  - 启动线程

    ```java
    // MyRunnable类
    public class MyRunnable implements Runnable{
        @Override
        public void run(){
            // 线程启动后执行的代码
            for(int i = 0; i < 100; i++){
                System.out.println("线程开启了" + i);
            }
        }
    }
    ```

    ```java
    // 测试类
    public class Demo{
        public static void main(String[] args){
            // 创建了一个参数的对象
            MyRunnable mr = new MyRunnable();
            // 创建了一个线程对象，并把参数传递给这个线程
            // 在线程启动之后，执行的就是参数里面的run方法
            Thread t = new Thread(mr);
            t.start();
            
            MyRunnable mr2 = new MyRunnable();
            Thread t2 = new Thread(mr2);
            t2.start();
        }
    }
    ```

- 利用Callable和Future接口方式实现

  - 定义一个MyCallable实现Callable接口

  - 在MyCallable类中重写call()方法

  - 创建Mycallable类的对象

  - 创建Future的实现类FutureTask对象，把Mycallable对象作为构造方法的参数

  - 创建Thread类的对象，把FutureTask对象作为构造方法的参数

  - 启动线程

    ```java
    // MyCallable类
    public class MyCallable implements Callable<String>{
        @Override
        public String call() throws Exception{
            for(int i = 0; i < 100; i++){
                System.out.println("线程启动了" + i);
            }
            // 返回值就表示线程运行完毕之后的结果
            return "完成";
        }
    }
    ```

    ```java
    // 测试类
    public class Demo{
        public static void main(String[] args){
            // 线程开启之后执行里面的call方法
            MyCallable mc = new MyCallable();
            // 可以获取线程执行完毕之后的结果，也可以作为参数传递给Thread对象
            FutureTack<String> ft = new FutureTask<>(mc);
            // 创建线程对象
            Thread t = new Thread(ft);
            // 开启线程
            ft.start();
            // 获取线程执行完毕返回的结果
            String s = ft.get();		// get方法不能在start方法前执行
            System.out.println(s);
        }
    }
    ```

#### 三种方式的对比

|                            | 优点                                         | 缺点                                       |
| -------------------------- | :------------------------------------------- | ------------------------------------------ |
| 实现Runnable、Callable接口 | 扩展性强，实现该接口的同时还可以继承其他的类 | 编程相对复杂，不能直接使用Thread类中的方法 |
| 继承Thread类               | 编程比较简单，可以直接使用Thread类中的方法   | 可扩展性较差，不能再继承其他的类           |

#### 线程类的常见方法

- 获取线程的名称
  - `String getName()`：返回此线程的名称
  - 如果不设置名称，默认Thread-数字
- 设置线程的名字
  - `void setName(String name)`：将此线程的名称更改为等于参数name
  - 通过构造方法也可以设置线程名称
- 获得当前线程对象
  - `public static Thread currentThread()`：返回对当前正在执行的线程对象的引用
- 线程休眠
  - `public static void sleep(long time)`：让线程休眠指定的时间，单位为毫秒

#### 线程调度

- 多线程的并发运行
  - 计算机中的CPU，在任意时刻只能执行一条机器指令。每个线程只有获得CPU的使用权才能执行代码。
    各个线程轮流获得CPU的使用权，分别执行各自的任务。
- 线程有两种调度模型
  - 分时调度模型：所有线程==轮流==使用CPU的使用权，平均分配每个线程占用CPU的时间片
  - 抢占式调度模型：优先让优先级高的线程使用CPU，如果线程的优先级相同，那么会==随机==选择一个，优先级高的线程获取的CPU时间片相对多一些
  - Java采用的是抢占式调度模型
- 线程的优先级
  - `public final void setPriority(int Priority)`：设置线程的优先级,默认优先级为5,范围为[1,10]
  - `public final int getPriority()`：获取线程的优先级

#### 后台线程/守护线程

- `public final void setDaemon(boolean on)`：设置为守护线程
- 当主要线程执行完毕之后，守护线程也没有继续执行下去的必要了
  但守护线程不会在主线程执行完毕后立即停止，因为他还占有着CPU的 使用权，还会再执行一会

### 线程安全问题

- 案例：卖票
  需求：某电影院目前正在上映国产大片，共有100张票，而它有3个窗口卖票，请设计一个程序模拟该电影院卖票
  思路

  - 定义一个类Ticket实现Runnable接口，里面定义一个成员变量：`private int ticketCount = 100;`
  - 在Ticket类中重写run()方法实现卖票，代码步骤如下
    - 判断票数大于0，就卖票，并告知是哪个窗口卖的
    - 票数减一
    - 卖光之后，线程停止
  - 定义一个测试类TicketDemo，里面有main方法，代码步骤如下
    - 创建Ticket类的对象
    - 创建三个Thread类的对象，把Ticekt对象作为构造方法的参数，并给出对应的窗口名称
    - 启动线程

  ```java
  // Ticket类
  public class Ticket implements Runnable{
  	private int ticket = 100;
  	@Override
  	public void run() {
  		// TODO Auto-generated method stub
  		while(true){
  			if(ticket == 0){
  				// 卖完了
  				break;
  			}else{
  				ticket--;
  				System.out.println(Thread.currentThread().getName() + "正在卖票，当前还剩余：" + ticket + "张票");
  			}
  		}
  	}
  	
  }
  
  ```

  ```java
  // Demo类
  public class Demo {
  	public static void main(String[] args){
  		// 为了多个线程共享一个类中的数据，所以只需要创建一个ticket对象
          Ticket ticket = new Ticket();
  		
  		Thread t1 = new Thread(ticket);
  		Thread t2 = new Thread(ticket);
  		Thread t3 = new Thread(ticket);
  		
  		t1.setName("窗口1");
  		t2.setName("窗口2");
  		t3.setName("窗口3");
  		t1.start();
  		t2.start();
  		t3.start();
  	}
  }
  ```

- 卖票案例的思考

  在实际生活中，售票时出票也是需要时间的，所以在出售一张电影票的时候，需要一点时间的延迟，假定每次出票时间为100毫秒，可使用`sleep()`方法实现

  - 问题
    - 相同的票出现了很多次
    - 出现了负数票数
  - 原因：在睡眠期间，其他线程抢占CPU使用权，因为都操作的是同一个数据，导致--的时候出现负数

- 卖票案例数据安全问题的解决
  为什么出现问题?（这也是判断多线程程序是否会有数据安全问题的标准）
  
  - 多线程操作共享数据
  
- 如何解决多线程安全问题呢？

  - 基本思想：让程序没有安全问题的环境
  - 怎么实现呢？
    把多条语句操作共享数据的代码给锁起来，让任意时刻只能有一个线程执行即可
    Java中提供了同步代码块的方式来解决

#### 同步代码块

- 锁多条语句操作共享数据，可以使用同步代码块来实现

- 格式

  ```java
  synchronized(任意对象){			// 锁的对象一定要是唯一的
      多条语句操作共享数据的代码
  }
  ```

- 锁默认情况是打开的，只要有一个线程进去执行代码了，锁就会关闭
- 当线程执行完毕出来了，锁才会自动打开
- 同步的好处和弊端
  - 好处：解决了多线程的数据安全问题
  - 弊端：当线程很多的时候，因为每个线程都会去判断同步上的锁，这是很耗费资源的，无形中会降低程序的运行效率

#### 同步方法

- 同步方法：就是把synchronized关键字加到方法前
- 格式：`修饰符 synchronized 返回值类型 方法名(方法参数){ }`
- 同步代码块和同步方法的区别
  - 同步代码块可以锁住指定代码，同步方法是锁住方法中的所有代码
  - 同步代码块可以指定锁对象，同步方法不能指定锁对象
  - 同步方法的锁对象为：`this`
    同步静态方法的锁对象为：`类名.class`        表示字节码文件的对象

#### Lock锁

- 虽然可以理解同步代码块和同步方法的锁对象问题，但是并没有直接看到在哪里加上了锁，在哪里释放了锁，为了更清晰的表达如何加锁和释放锁，JDK5以后提供了一个新的锁对象Lock
  Lock实现提供比使用synchronized方法和语句可以获得更广泛的锁定操作
- Lock中提供了获得锁和释放锁的方法
  - `void lock()`：获得锁
  - `void unlock()`：释放锁
- Lock是接口不能直接实例化，这里采用它的实现类==ReentrantLock==
  ReentrantLock的构造方法：`ReentrantLock()`

#### 死锁

- 线程死锁是指由于两个或者多个线程互相持有对方所需要的资源，导致这些线程处于等待状态，无法前往执行
- 解决方法：不要写锁的嵌套即可

### 生产者和消费者

- 概述：生产者消费者模式是一种十分经典的多线程协作的模式，弄懂生产者消费者问题能够让我们对多线程编程的理解更加深刻

- 等待和唤醒的方法
  为了体现生产和消费过程中的等待和唤醒，Java提供了几个方法供我们使用，这几个方法在Object类中

  | 方法名           | 说明                                                         |
  | ---------------- | ------------------------------------------------------------ |
  | void wait()      | 导致当前线程等待，直到另一个线程调用该对象的notify()方法或notifyAll()方法 |
  | void notify()    | 唤醒正在等待对象监视器的单个线程                             |
  | void notifyAll() | 唤醒正在等待对象监视器的所有线程                             |

- 代码实现
  套路：

  - while(true)死循环
  - synchronized 锁，锁对象要唯一
  - 判断，共享数据是否结束

  ```java
  /*消费者步骤：
  1.判断桌子上是否有汉堡包
  2.如果没有就等待
  3.如果有就开吃
  4.吃完之后，桌子上的汉堡包就没有了
  	叫醒等待的生产者继续生产
  汉堡包的总数量减一*/
  
  /*生产者步骤：
  1.判断桌子上是否有汉堡包
  	如果有就等待，没有就生成
  2.把汉堡包放在桌子上
  3.叫醒等待的消费者开吃*/
  ```

  ```java
  // Desk类
  package ThreadDemo;
  
  package ThreadDemo;
  
  public class Desk {
  	// 状态：桌上有无汉堡包
  	private boolean flag;
  	// 数量
  	private int count;
  	// 锁对象
  	private final Object lock = new Object();
  	public Desk(boolean flag, int count) {
  		super();
  		this.flag = flag;
  		this.count = count;
  	}
  	public Desk() {
  		super();
  	}
  	public boolean isFlag() {
  		return flag;
  	}
  	public void setFlag(boolean flag) {
  		this.flag = flag;
  	}
  	public int getCount() {
  		return count;
  	}
  	public void setCount(int count) {
  		this.count = count;
  	}
  	public Object getLock() {
  		return lock;
  	}
  	@Override
  	public String toString() {
  		return "Desk [flag=" + flag + ", count=" + count + ", lock=" + lock + "]";
  	}	
  }
  ```

  ```java
  // 吃货类
  package ThreadDemo;
  
  public class Foodie extends Thread{
  	private Desk desk;
  	
  	public Foodie(Desk desk) {
  		super();
  		this.desk = desk;
  	}
  	
  	public void run(){
  		while(true){
  			synchronized(desk.getLock()){
  				if(desk.getCount() == 0){
  					break;
  				}else{
  					if(desk.isFlag()){		// 桌上有就开吃
  						System.out.println("吃货正在吃汉堡包");
  						desk.setCount(desk.getCount() - 1);
  						desk.setFlag(false);
  						desk.getLock().notifyAll();   // 叫醒厨师继续生产
  					}else{		// 如果没有就等待
  						try {
  							desk.getLock().wait();
  						} catch (InterruptedException e) {
  							// TODO Auto-generated catch block
  							e.printStackTrace();
  						}
  					}
  				}
  			}
  		}
  	}
  }
  ```

  ```java
  // 厨师类
  package ThreadDemo;
  
  public class Cooker extends Thread{
  	private Desk desk;
  	
  	public Cooker(Desk desk) {
  		super();
  		this.desk = desk;
  	}
  
  	public void run(){
  		while(true){
  			synchronized(desk.getLock()){
  				if(desk.getCount() == 0){
  					break;
  				}else{
  					if(!desk.isFlag()){		// 桌上没有汉堡包就生产
  						System.out.println("厨师正在生产第" + (11 - desk.getCount()) + "个汉堡包");
  						desk.setFlag(true);
  						desk.getLock().notifyAll();		// 叫醒吃货来吃汉堡包
  					}else{			// 有就等待
  						try {
  							desk.getLock().wait();
  						} catch (InterruptedException e) {
  							// TODO Auto-generated catch block
  							e.printStackTrace();
  						}
  					}
  				}
  			}
  		}
  	}
  }
  
  ```

  ```java
  // 测试类
  package ThreadDemo;
  
  public class Demo {
  	
  	public static void main(String[] args){
  		Desk desk = new Desk(false, 10);
  		Foodie fd = new Foodie(desk);
  		Cooker ck = new Cooker(desk);
  		fd.start();
  		ck.start();
  	}
  }
  ```

- 阻塞队列实现等待唤醒机制

  - 阻塞队列继承结构
    Iterable(接口) -> Collection(接口) -> Queue(接口) -> BlockingQueue(接口) -> ArrayBlockingQueue(实现类) / LinkedBlockingQueue(实现类)

  - BlockingQueue的核心方法：
    `put(anObject)`：将参数放入队列，如果放不进去会阻塞
    `take()`：取出第一个参数，取不到会阻塞

  - 常见BlockingQueue：
    `ArrayBlockingQueue`：底层是数组，有界
    `LinkedBlockingQueue`：底层是链表，无界。但不是真正的无界，最大为int的最大值

  - 代码实现

    ```java
    // 吃货类
    package ThreadDemo2;
    
    import java.util.concurrent.ArrayBlockingQueue;
    
    public class Foodie extends Thread{
    	private ArrayBlockingQueue<String> list;
    	
    	
    	public Foodie(ArrayBlockingQueue<String> list) {
    		super();
    		this.list = list;
    	}
    
    
    	public void run(){
    		while(true){
    			try {
    				System.out.println("吃货吃了一个" + list.take());
    			} catch (InterruptedException e) {
    				// TODO Auto-generated catch block
    				e.printStackTrace();
    			}
    		}
    	}
    }
    ```

    ```java
    // 厨师类
    package ThreadDemo2;
    
    import java.util.concurrent.ArrayBlockingQueue;
    
    public class Cooker extends Thread{
    	private ArrayBlockingQueue<String> list;
    
    	public Cooker(ArrayBlockingQueue<String> list) {
    		super();
    		this.list = list;
    	}
    
    	@Override
    	public void run() {
    		while(true){
    			try {
    				list.put("汉堡包");
    				System.out.println("厨师放了一个汉堡包");
    			} catch (InterruptedException e) {
    				// TODO Auto-generated catch block
    				e.printStackTrace();
    			}
    		}
    	}
    	
    	
    }
    
    ```

    ```java
    // 测试类
    package ThreadDemo2;
    
    import java.util.concurrent.ArrayBlockingQueue;
    
    public class Demo {
    
    	public static void main(String[] args) {
    		// 创建一个阻塞队列，容量为1
    		ArrayBlockingQueue<String> list = new ArrayBlockingQueue<>(1);
    		
    		// 创建相应的生产者和消费者
    		Foodie fd = new Foodie(list);
    		Cooker ck = new Cooker(list);
    		
    		// 开启对应的线程
    		ck.start();
    		fd.start();
    	}
    
    }
    ```

### 线程池&volatile

#### 线程状态

![](E:\Typora\学习笔记\images\线程状态.png)

- 虚拟机中线程的六种状态
  - 新建状态（NEW）			------			创建线程对象
  - 就绪状态（RUNNABLE）				------					start方法
  - 阻塞状态（BLOCKED）			-------   无法获得锁对象
  - 等待状态（WAITING）           ---------   wait方法
  - 计时等待（TIMED_WAITING）            -------- sleep等方法
  - 结束状态（TERMINATED）              --------     全部代码运行完毕

#### 线程池

- 以前写多线程的弊端

  - 用到线程的时候就创建
  - 用完之后线程消失

- 解决方案

  - 创建一个池子（线程池），池子是空的-------创建Executors中的静态方法

  - 有任务需要执行时，才会创建线程对象
    当任务执行完毕，线程对象归还给池子----------submit方法

  - 所有任务全部执行完毕，关闭连接池---------shutdown方法

    > 池子会自动的帮我们创建对象，任务执行完毕，也会自动把线程对象归还池子
    >
    > Executors----------可以帮助我们创建线程池对象
    >
    > ExecutorService---------可以帮助我们控制线程池

- 代码实现

  - `static ExecutorService newCachedThreadPool()`：创建一个默认的线程池，池子中默认是空的，默认最多可容纳int类型的最大值

  - `static newFixedThreadPool(int nThreads)`：创建一个指定最多线程数量的线程池

  - ```java
    package Executor;
    
    import java.util.concurrent.ExecutorService;
    import java.util.concurrent.Executors;
    
    public class Demo1 {
    
    	public static void main(String[] args) throws InterruptedException {
    		// 创建一个线程池对象
    		ExecutorService executorService = Executors.newCachedThreadPool();
            // ExecutorService executorService = Executors.newFixedThreadPool()
    		// 提交任务
    		executorService.submit(()->{
    			System.out.println(Thread.currentThread().getName() + "执行了");
    		});
    		
    		Thread.sleep(2000);
    		
    		executorService.submit(()->{
    			System.out.println(Thread.currentThread().getName() + "执行了");
    		});
    		
    		executorService.shutdown();
    	}
    
    }
    ```

- ThreadPoolExecutor

  - 核心元素

    - 核心线程数量（一旦创建，不能销毁，除非线程池整体被销毁）---------不能小于0
    - 线程池中的最大线程数量-------------不能小于等于0，最大数量>=核心线程数量
    - 空闲线程最大存活时间-------------不能小于0
    - 时间单位-------------时间单位，使用TimeUnit的静态属性
    - 任务队列--------不能为null
    - 创建线程工厂---------------不能为null
    - 任务的拒绝策略-----------------不能为null
      ThreadPoolExecutor.AbortPolicy-----丢弃任务并抛出RejectedExecutionException异常，是==默认的==策略
      ThreadPoolExecutor.DiscardPolicy----丢弃任务，但是不抛出异常。不推荐的做法
      ThreadPoolExecutor.DiscardOldestPolicy-----抛弃队列中等待最久的任务，然后把当前的任务加入队列中
      ThreadPoolExecutor.CallerRunsPolicy----调用任务的run()方法绕过线程池直接执行

  - 代码实现

    ```java
    package ThreadPool;
    
    import java.util.concurrent.ArrayBlockingQueue;
    import java.util.concurrent.Executors;
    import java.util.concurrent.ThreadPoolExecutor;
    import java.util.concurrent.TimeUnit;
    
    public class MyThreadPoolDemo {
    
    	public static void main(String[] args) {
    		ThreadPoolExecutor pool = new ThreadPoolExecutor(
    				2,
    				5,
    				2,
    				TimeUnit.SECONDS,
    				new ArrayBlockingQueue<>(10),
    				Executors.defaultThreadFactory(),
    				new ThreadPoolExecutor.AbortPolicy());
    		pool.submit(()->{
    			System.out.println(Thread.currentThread().getName() + "在执行");
    		});
    		pool.submit(()->{
    			System.out.println(Thread.currentThread().getName() + "在执行");
    		});
    		pool.shutdown();
    	}
    }
    ```

#### Volatile

- 问题描述
  当A线程修改了共享数据时，B线程没有及时获取到最新的值，如果还在使用原先的值，就会出现问题
- JMM
  - 在Java虚拟机中，堆内存是唯一的，而每一个线程都有自己独立的栈内存
  - 每一个线程在使用堆里面的变量的时候，都会先拷贝一份到变量的副本中
  - 在线程中，每一次使用的是从变量的副本中获取的
- Volatile关键字：强制线程在每次使用的时候，都会看一下共享区域最新的值
- 问题解决方案
  - Volatile关键字
  - synchronized同步代码块（也具有强制线程查看共享数据中的最新值）
    - 线程获得锁
    - 清空变量副本
    - 拷贝共享变量最新的值到变量副本中
    - 执行代码
    - 将修改后变量副本的值赋给共享数据
    - 释放锁

### 原子性&并发工具类

- 所谓原子性是指在一次或多次操作中，要么所有的操作全部都得到了执行并且不会受到任何因素的干扰而中断，要么所有的操作都不执行，==多个操作是一个不可分割的整体==

  > count++不是一个原子性操作，也就是说他在执行的过程中，有可能被其他线程打断操作
  >
  > volatile关键字不能保证原子性，只能保证每次线程共享数据的时候是最新值
  >
  > ==synchronized同步代码块可以保证原子性，但是速度相对比较慢==

#### 原子类AtomicInteger

|                 方法名                 |                             说明                             |
| :------------------------------------: | :----------------------------------------------------------: |
|         public AtomicInteger()         |              初始化一个默认值为0的原子型Integer              |
| public AtomicInteger(int initialValue) |               初始化一个指定值的原子型Integer                |
|               int get()                |                            获取值                            |
|         int getAndIncrement()          |     以原子方式将当前值加1，注意，这里返回的是自增前的值      |
|         int incrementAndGet()          |     以原子方式将当前值加1，注意，这里返回的是自增后的值      |
|        int addAndGet(int data)         | 以原子方式将输入的数值与实例中的值(AtomicInteger里的value)相加，并返回结果 |
|        int getAndSet(int value)        |           以原子方式设置为newValue的值，并返回旧值           |

```java
// MyAtomThread类
public class MyAtomThread implements Runnable{
   AtomicInteger ac = new AtomicInteger();
   
    public void run(){
        for(int i = 0; i < 100; i++){
            int count = ac.incrementAndGet();
            System.out.println("已经送了" + count + "个冰淇淋");
        }
    }
}
```

```java
// 测试类
public class Demo{
    public static void main(String[] args){
        MyAtomThread atom = new MyAtomThread();
        
        for(int i = 0; i < 100; i++){
            new Thread(atom).start();
        }
    }
}
```

#### AtomicInteger原理

- 自旋锁 + CAS算法
- CAS算法：有3个操作数(内存值V, 旧的预期值A, 要修改的值B)
  - 当旧的预期值A == 内存值  此时修改成功，将V改为B
  - 当旧的预期值A != 内存值  此时修改失败，不做任何操作
  - 并重新获取现在的最新值(这个重新获取的动作就是自旋)

#### 悲观锁和乐观锁

- synchronized和CAS的区别
  - 相同点：在多线程情况下，都可以保证共享数据的安全性
  - 不同点
    - synchronized总是从最坏的角度出发，认为每次获取数据的时候，别人都有可能修改，所以每次操作共享数据之前，都会上锁。（**悲观锁**）
    - CAS是从乐观的角度出发，假设每次获取数据别人都不会修改，所以不会上锁。只不过在修改共享数据的时候，会检查一下，别人有没有修改过这个数据。（**乐观锁**）
      如果别人修改过，就再次获取最新值（==自旋==）
      如果别人没有修改过，就直接修改

#### 并发工具类

- Hashtable
  HashMap是线程不安全的（多线程环境下可能会存在问题）
  为了保证数据的安全性我们可以使用Hashtable，但是Hashtable的效率低下
  - Hashtable采取悲观锁synchronized的形式保证数据的安全性
  - 只要有线程访问，会将整张表全部锁起来，所以Hashtable的效率低下

- ConcurrentHashMap
  - ConcurrentHashMap是线程安全的，而且效率也比较高，继承于Map
  - JDK1.7原理解析
    - 创建对象
      - 创建一个默认长度16，默认加载因子0.75的数组，数组名Segment，这个大数组一旦创建，无法扩容
      - 再创建一个长度为2的小数组，把地址值赋值给0索引，其它索引都为null
    - 添加
      - 第一次会根据键的哈希值计算出在大数组中应存入的位置
        如果为null，则按照模板创建小数组
        创建完毕，会二次哈希，计算出在小数组中应存入的位置，直接存入
      - 如果不为null，就会根据记录的地址值找到小数组
        二次哈希，计算出在小数组中应存入的位置
        如果需要扩容，则将小数组扩容两倍
        如果不需要扩容，则判断小数组的这个位置有没有元素
              如果没有元素，则直接存
              如果有元素，则会调用equals方法，比较属性值
                   如果equals为true，则不存
                   如果equals为false，则形成哈希桶结构
  - JDK1.8原理解析
    - 底层结构：哈希表（数组、链表、红黑树的结合体）
    - 结合CAS机制 + synchronized同步代码块形式保证线程安全
    - 总结
      - 如果使用空参构造创建ConcurrentHashMap对象，则什么事情都不做
        在第一次添加元素的时候创建哈希表
      - 计算当前元素应存入的索引
      - 如果该索引位置为null，则利用CAS算法，将本结点添加到数组中
      - 如果该索引位置不为null，则利用volatile关键字获得当前位置最新的结点地址，挂在他下面，形成链表
      - 当链表的长度大于等于8时，自动转换为红黑树
      - 以链表或者红黑树头结点为锁对象，配合悲观锁保证多线程操作集合时数据的安全性

- CountDownLatch

  - 使用场景：让某一条线程等待其他线程执行完毕后再执行

    |              方法名              |                         说明                         |
    | :------------------------------: | :--------------------------------------------------: |
    | public CountDownLatch(int count) | 参数传递线程数，表示等待线程数量。并定义了一个计数器 |
    |       public void await()        |     让线程等待，当计数器为0时，会唤醒等待的线程      |
    |     public void countDown()      |           当前线程执行完毕，会将计数器减一           |

- Semaphore
  - 使用场景：可以控制访问特定资源的线程数量
  - 步骤
    - 创建Semaphore对象：`new Semaphore(int n)`----n表示最多可发放通行证的数量
    - acquire()方法发放通行证
    - release()方法收回通行证

## 网络编程

### 网络编程入门

- 网络编程：在网络通信协议下，不同计算机上运行的程序，可以进行数据传输
- 网络编程三要素
  - IP地址：设备在网络中的地址，是唯一的标识
  - 端口：应用程序在设备中唯一的标识
  - 协议：数据在网络中传输的规则，常见的协议有UDP和TCP协议

#### IP

- IP：全称“互联网协议地址”，也称IP地址。是分配给上网设备的数字标签。常见的IP分类为：ipv4和ipv6
  通过域名访问服务器->域名通过DNS服务器解析为IP地址传递回去->计算机再通过解析好的IP地址访问相应的服务器->服务器返回数据展示在浏览器上

- IPv4

  - 32bit(4字节)：1 100000000 10101000 00000001 01000010
    点分十进制表示法：192.168.1.66

- IPv6

  - 由于互联网的蓬勃发展，IP地址的需求量愈来愈大，而IPv4的模式下IP的总数是有限的。
    采用128位地址长度，分成8组，每16位分为一组

  - 冒分十六进制表示法：2001:0DB8:0000:0023:0008:0800:200C:417A
    省略前面的0：2001:DB8:0:23:8:800:200C:417A

  - 特殊情况：如果计算出的16进制表示形式中间有多个连续的0(FF01:0:0:0:0:0:0:1101)

    ​					采用0位压缩表示法:FF01::1101

- 常用命令
  - `ipconfig`：查看本机IP地址
  - `ping IP地址`：检查网络是否连通

#### InetAddress的使用

- 为了方便我们对IP地址的获取和操作，Java提供了一个类InetAddress供我们使用
- InetAddress：此类表示Internet协议(IP)地址
- 常用方法
  - `static InetAddress getByName(String host)`：确定主机名称的IP地址。主机名称可以是机器名称，也可以是IP地址
  - `String getHostName()`：获取此IP地址的主机名
  - `String getHostAddress()`：返回文本显示中的IP地址字符串

#### 端口

- 端口：应用程序在设备中唯一的标识
- 端口号：用两个字节表示的整数，它的取值范围是0~65535
  				其中0~1023之间的端口号用于一些知名的网络服务或者应用
        				在自己使用时使用1024以上的端口号就可以了
- 注意：一个端口号只能被一个应用程序使用

#### 协议

- 在计算机网络中，连接和通信的规则被称为网络通信协议
- UDP协议
  - 用户数据报协议(User Datagram Protocol)
  - UDP是==面向无连接==通信协议
    速度快，有大小限制，一次最多发送64K，数据不安全，容易丢失数据
- TCP协议
  - 传输控制协议(Transmission Control Protocol)
  - TCP协议是==面向连接==的通信协议
    速度慢，没有大小限制，数据安全

### UDP通讯程序

- 发送端：发送数据
  接收端：接收数据

#### UDP发送端

- 发送数据步骤
  - 创建发送端的DatagramSocket对象
  - 创建数据，并把数据打包(DatagramPacket)
  - 调用DatagramSocket对象的方法发送数据
  - 释放资源
- 代码实现

```java
public class Demo{
    public static void main(String[] args) throws IOException{
        // 创建发送端对象
    	DatagramSocket ds = new DatagramSocket();
    	// 数据打包   DatagramPacket(byte[] buf, int length, InetAddress, int port)
    	String s = "需要发送的数据";
    	byte[] bytes = s.getBytes();
    	InetAddress address = InetAddress.getByName("127.0.0.1");
    	int port = 10000;
    	DatagramPacket dp = new DatagramPacket(bytes, bytes.length, address, port);
    	// 发送数据
    	ds.send(dp);
    	// 释放资源
    	ds.close();
    }
}
```

#### UDP接收端

- 步骤
  - 创建接收端的DatagramSocket对象
  - 创建一个箱子，用于接收数据
  - 调用DatagramSocket的方法接收数据并将数据放入箱子中
  - 解析数据包，并把数据在控制台显示
  - 释放资源
- 代码

```java
public class Demo{
    public static void main(String[] args) throws{
        // 创建接收端对象------参数表示从10000端口接收数据
        DatagramSocket ds = new DatagramSocket(10000);
        // 创建箱子
        byte[] bytes = new bytes[1024];
        DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
        // 接收数据
        ds.receive(dp);
        // 获取数据
        byte[] data = dp.getData();
        System.out.println(new String(data));
        // 释放资源
        ds.close();
    }
}
```

> 在这里运行时必须先运行接收端再运行发送端(否则都发送完了才运行接收端就接收不到了)
>
> 如果接收端在启动之后没有接收到数据，会阻塞
>
> 在接收数据的时候，需要调用一个getLength方法，表示接收到了多少字节

#### UDP练习

- UDP发送数据：数据来自于键盘录入，直到输入的数据是886，发送数据结束
- UDP接收端：因为不知道发送端什么时候停止发送，就死循环接收

```java
// 发送端
package UDP;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.net.SocketException;
import java.net.UnknownHostException;
import java.util.Scanner;

public class ClientDemo {
	public static void main(String[] args) throws IOException{
		Scanner sc = new Scanner(System.in);
		DatagramSocket ds = new DatagramSocket();
		while(true){
			String s = sc.nextLine();
			if("886".equals(s)) break;
			byte[] bytes = s.getBytes();
			InetAddress address = InetAddress.getByName("127.0.0.1");
			int port = 10000;
			DatagramPacket dp = new DatagramPacket(bytes, bytes.length, address, port);
			ds.send(dp);
		}
		ds.close();
	}
}
```

```java
// 接收端
package UDP;

import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.SocketException;

public class ServerDemo {

	public static void main(String[] args) throws IOException {
		DatagramSocket ds = new DatagramSocket(10000);
		while(true){
			byte[] bytes = new byte[1024];
			DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
			ds.receive(dp);
			byte[] data = dp.getData();
			int length = dp.getLength();
			System.out.println(new String(data, 0, length));
		}
		// ds.close();
	}
}
```

#### 三种通信方式

- 单播：一个发送端通过一个路由器只发送给一个接收端（一对一）
- 组播：一个发送端通过一个路由器发送给一组接收端（一对多）
  - 组播地址：224.0.0.0~239.255.255.255
    					其中224.0.0.0~224.0.0.255为预留的组播地址，不可用
  - 组播的发送端在调用DatagramSocket对象的方法发送数据时，单播是发送给指定IP的电脑，组播是发送给组播地址
  - 组播的接收端创建的是MulticastSocket对象
    在创建箱子后，还要把当前电脑添加到这一组中

```java
// 组播的发送端
public static void main(String[] args) throws IOException{
    DatagramSocket ds = new DatagramSocket();
    String s = "Hello Word";
    byte[] bytes = s.getBytes();
    InetAddress address = InetAddress.getByName("224.0.1.0");
    int port = 10000;
    DatagramPacket dp = new DatagramPacket(bytes, bytes.length, address, port);
    ds.send(dp);
    ds.close();
}
```

```java
// 接收端
public static void main(String[] args) throws IOException{
    MulticastSocket ms = new MulticastSocket(10000);
    DatagramPacket dp = new DatagramPacket(new byte[1024], 1024);
    // 把当前计算机绑定一个组播地址
    ms.joinGroup(InetAddress.getByName("224.0.1.0"));
    
    // 接收数据
    ms.receive(dp);
    byte[] data = dp.getData();
    int length = dp.getLength();
    System.out.println(new String(data, 0, length));
    ms.close();
}
```

- 广播：一个发送端通过一个路由器发送给该局域网下所有接收端（一对所有）
  - 广播地址：255.255.255.255

```java
// 发送端
public static void main(String[] args) throws IOException{
    DatagramSocket ds = new DatagramSocket();
    String s = "广播发送端";
    byte[] bytes = s.getBytes();
    InetAddress address = InetAddress.getByName("255.255.255.255");
    int port = 10000;
    DatagramPacket dp = new DatagramPacket(bytes, bytes.length, address, port);
    ds.sent(dp);
    ds.close();
}
```

```java
// 接收端
public class ServerDemo {

	public static void main(String[] args) throws IOException {
		DatagramSocket ds = new DatagramSocket(10000);
		while(true){
			byte[] bytes = new byte[1024];
			DatagramPacket dp = new DatagramPacket(bytes, bytes.length);
			ds.receive(dp);
			byte[] data = dp.getData();
			int length = dp.getLength();
			System.out.println(new String(data, 0, length));
		}
		ds.close();
	}
}
```

### TCP通讯程序

- TCP通信协议是一种可靠的网络协议，它在通信的两端各建立一个Socket对象
  发送端：`Socket`					接收端：`ServerSocket`

  通信之前要保证连接已经建立
  通过Socket产生IO流来进行网络通信

#### 发送数据

- 创建客户端的Socket对象(Socket)与指定服务端连接
  `Socket(String host, int port)`

- 获取输出流，写数据
  `OutputStream getOutputStream()`

- 释放资源
  `void close()`

- 代码实现

  ```java
  // 客户端
  public static void main(String[] args) throws IOException{
      
      Socket socket = new Socket("127.0.0.1", 10000);
      
      OutputStream os = socket.getOutputStream();
      os.write("hello".getBytes());
      
      os.close();
      socket.close();
  }
  ```

#### 接收数据

- 创建服务端的Socket对象(ServerSocket)
  `ServerSocket(int port)`

- 监听客户端连接，返回一个Socket对象
  `Socket accept()`

- 获得输入流，读数据，并把数据显示在控制台
  `InputStream getInputStream()`

- 释放资源
  `void close()`

- 代码实现

  ```java
  // 服务端
  public static void main(String[] args){
      ServerSocket ss = new ServerSocket(10000);
      
      Socket accept = ss.accept();		// 没有客户端连接的话，就会死等，不执行后续代码，即阻塞
      
      InputStream is = accept.getInputStream();
      int b;
      while((b = is.read()) != -1){
          System.out.print((char) b);
      }
      
      is.close();
      ss.close();
  }
  ```

#### 原理分析

- 不能先运行客户端（先运行客户端会没有服务端可连，就会报错）
- 先运行服务端，代码会依次执行到accept方法，然后就阻塞，等待客户端连接
- 运行客户端，在对象创建完毕之后，客户端与服务端的连接通道就已经建立
  客户端写数据，服务端读数据
- 客户端释放资源，服务端释放资源

>客户端创建对象并连接服务器，此时是通过三次握手协议保证服务器之间的连接
>
>针对客户端，是往外写的，所以是输出流；而服务端是往进读的，所以是输入流
>
>read方法也是阻塞的
>
>在关流的时候，还多了一个往服务器写结束标记的动作
>
>最后一步断开连接，会通过四次挥手协议保证连接终止

#### 三次握手

- 保证客户端与服务器之间建立连接

- 第一次：客户端向服务器发出连接请求（等待服务器确认）
- 第二次：服务器向客户端返回一个响应（告诉客户端收到了请求）
- 第三次：客户端向服务端再次发出确认信息（连接建立）

#### 四次挥手

- 保证客户端与服务端取消连接，成功终止连接
- 第一次：客户端向服务器发出取消连接请求
- 第二次：服务器向客户端返回一个响应，表示收到客户端取消请求
  				服务器将最后的数据处理完毕
- 第三次：服务器向客户端发出确认取消信息
- 第四次：客户端再次发送确认消息（连接取消）

#### 练习

- 练习一

  - 客户端：发送数据，接收服务器反馈

  - 服务器：接收数据，给出反馈

  - 代码

    ```java
    // 客户端
    package TCP;
    
    import java.io.IOException;
    import java.io.InputStream;
    import java.net.Socket;
    import java.net.UnknownHostException;
    import java.io.OutputStream;
    
    
    public class ClientDemo {
    
    	public static void main(String[] args) throws IOException {
    		Socket socket = new Socket("127.0.0.1", 10000);
    		
    		OutputStream os = socket.getOutputStream();
    		os.write("hello".getBytes());
    		socket.shutdownOutput();    // 仅仅关闭输出流，并写一个结束标记，对socket没有任何影响
    		
    		InputStream is = socket.getInputStream();
    		int b;
    		while((b = is.read()) != -1){
    			System.out.print((char)b);
    		}
    		
    		is.close();
    		os.close();
    		socket.close();
    
    	}
    }
    ```

    ```java
    // 服务端
    package TCP;
    
    import java.io.IOException;
    import java.io.OutputStream;
    import java.net.ServerSocket;
    import java.net.Socket;
    
    import java.io.InputStream;
    
    public class ServerDemo {
    
    	public static void main(String[] args) throws IOException {
    		ServerSocket ss = new ServerSocket(10000);
    		
    		Socket accept = ss.accept();
    		
    		InputStream is = (InputStream) accept.getInputStream();
    		int b;
    		while((b = is.read()) != -1){
    			System.out.print((char)b);
    		}
    		
    		OutputStream os = accept.getOutputStream();
    		os.write("who?".getBytes());
    		
    		os.close();
    		is.close();
    		accept.close();
    		ss.close();
    
    	}
    }
    ```

- 练习二

  - 客户端：将本地文件上传到服务器，接收服务器的反馈

  - 服务器：接收客户上传的文件，上传完毕之后给出反馈

  - 代码

    ```java
    // 客户端
    package TCP;
    
    import java.io.BufferedInputStream;
    import java.io.BufferedOutputStream;
    import java.io.BufferedReader;
    import java.io.FileInputStream;
    import java.io.IOException;
    import java.io.InputStreamReader;
    import java.io.OutputStream;
    import java.net.Socket;
    
    public class ClientDemo2 {
    
    	public static void main(String[] args) throws IOException {
    		Socket socket = new Socket("127.0.0.1", 10000);
    		
    		// 本地的流，读取本地文件
    		BufferedInputStream bis = new BufferedInputStream(new FileInputStream("1.png"));
    		
    		OutputStream os = socket.getOutputStream();
    		BufferedOutputStream bos = new BufferedOutputStream(os);
    		int b;
    		while((b = bis.read()) != -1){
    			bos.write(b);        // 通过网络写到服务器中
    		}
    		
    		// 给服务器一个结束标记
    		socket.shutdownOutput();
    		
    		BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
    		String line;
    		while((line = br.readLine()) != null){
    			System.out.println(line);
    		}
    		
    		socket.close();
    		bis.close();
    	}
    
    }
    
    ```
    
    ```java
    // 服务器
    package TCP;
    
    import java.io.BufferedInputStream;
    import java.io.BufferedOutputStream;
    import java.io.BufferedWriter;
    import java.io.FileOutputStream;
    import java.io.IOException;
    import java.io.OutputStreamWriter;
    import java.net.ServerSocket;
    import java.net.Socket;
    
    public class ServerDemo2 {
    
    	public static void main(String[] args) throws IOException {
    		ServerSocket ss = new ServerSocket(10000);
    		
    		Socket accept = ss.accept();
    		// 网络中的流，从客户端读取数据的
    		BufferedInputStream bis = new BufferedInputStream(accept.getInputStream());
    		// 本地的IO流，把数据写到本地中，实现永久化存储
    		BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("src\\copy.png"));
    		
    		int b;
    		while((b = bis.read()) != -1){
    			bos.write(b);
    		}
    		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(accept.getOutputStream()));
    		bw.write("上传成功！");
    		bw.newLine();
    		bw.flush();
    		
    		accept.close();
    		ss.close();
    		bos.close();
    	}
    
    }
    
    ```
    

### 服务端优化

- 第一个弊端：服务器只能处理一个客户端请求，接受完一个文件之后，服务器就关闭了
  改进方式：循环
- UUID
  - `UUID uuid = UUID.randomUUID();`       生成一个随机且唯一的uid
  - `uuid.toString();`       转换为字符串
  - 防止多次上传文件时，后上传的文件覆盖掉先上传的文件
- 仅仅使用while循环，无法同时处理多个客户端的请求
  采用多线程改进
- 使用多线程虽然可以让服务器同时处理多个客户端请求，但是资源消耗太大
  采用线程池改进

## 基础加强

### 类加载器&反射

#### 类加载器

- 概述：负责将.class文件（存储的物理文件）加载到内存中

- 加载时机

  - 创建类的实例（对象）
  - 调用类的类方法（静态方法）
  - 访问类或者接口的类变量，或者为该类变量赋值（静态变量）
  - 使用反射方式来强制创建某个类或接口对应的java.lang.Class对象
  - 初始化某个类的子类
  - 直接使用java.exe命令来运行某个主类

  ==用到就加载，不用不加载==

- 加载过程
  加载---验证---准备---解析---初始化

  > 又将验证---准备---解析这三步称为链接

  - 加载
    - 通过一个类的全限定名来获取定义此类的二进制字节流（包名+类名；用流进行传输）
    - 将这个字节流所代表的静态存储结构转化为运行时数据结构（将这个类加载到内存中）
    - 在内存中生成一个代表这个类的java.lang.Class对象，任何类被使用时，系统都会为之建立一个java.lang.Class对象（加载完毕创建一个class对象）
  - 链接
    - 验证：确保Class文件字节流中包含的信息符合当前虚拟机的要求，并且不会危害虚拟机自身安全（文件中的信息是否符合虚拟机规范、有没有安全隐患）
    - 准备：负责为类的类变量（静态变量）分配内存，并设置默认初始化值（初始化静态变量）
    - 解析：将类的二进制数据流中的符号引用替换为直接引用（本类中用到了其他类，此时就要找到对应的类）
  - 初始化：根据程序员通过程序制定的主观计划去初始化类变量和其他资源（静态变量赋值以及初始化其他资源）

- 分类

  - 启动类加载器(Bootstrap ClassLoader)：虚拟机内置的类加载器
  - 平台类加载器(Platform Classloader)：负责加载JDK中一些特殊的模块(继承启动类加载器)
  - 系统类加载器(System Classloader)：负责加载用户类路径上所指定的类库(继承平台类加载器)(==用的最多==)
  - 自定义类加载器(UserClassloader)：自定义的类加载器(继承系统类加载器)（==用的不多==）

- 双亲委派模型

  - 当使用最下层的类加载器加载字节码文件时，首先会把加载任务逐层委派给父类加载器，直到最顶层的启动类加载器中
  - 这些加载器都有各自的加载范围，当父类加载器无法完成加载请求时，就会一层层往下返回

  >  `ClassLoader systemClassLoader = ClassLoader.getSystemClassLoader();`----可以获得系统类加载器
  >
  > `systemClassLoader.getParent()`-------------得到父类加载器

- 常用方法

  | 方法名                                  | 说明                                                         |
  | --------------------------------------- | ------------------------------------------------------------ |
  | loadClass(String name, boolean resolve) | 加载指定名称(包括包名)的二进制类型                           |
  | findClass(String name)                  | 当loadClass方法中父类加载失败时，调用自己的findClass方法来完成类加载 |
  | defineClass(byte[] b, int off, int len) | 将byte字节流解析成JVM能够识别的Class对象                     |
  | resolveClass(Class<?> c)                | 让使用类的Class对象创建完成也同时被解析                      |

#### 反射

- Java反射机制
  在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法
  对于任意一个对象，都能够调用它的任意属性和方法
  这种==动态获取信息==以及==动态调用对象方法==的功能称为Java语言的**反射**机制

  > 利用反射调用它类中的属性和方法时，无视修饰符。反射操作，程序比较灵活，动态的
  >
  > 先获取配置文件中的信息，动态获取信息并创建对象和调用方法

- 获取Class对象

  | 以前调用一个类中的方法 |      反射调用一个类中的方法       |
  | :--------------------: | :-------------------------------: |
  | 创建这个类的对象(new)  | 反射方式：创建对象(利用Class对象) |
  |     用对象调用方法     |        反射方式：调用方法         |

  - 源代码阶段：`Class.forName(String className)`  通过Class类静态方法传递全类名获取Class对象
  - Class对象阶段：`类名.class`  
  - Runtime运行时阶段：`对象.getClass()`

- 获取Constructor对象

  - `Constructor<?>[] getConstructors()`：返回所有公共构造方法对象的数组
  - `Constructor<?>[] getDeclaredConstructors()` ：返回所有构造方法对象的数组（包括私有）
  - `Constructor<T> getConstructor(Class<?>... parameterTypes)`：返回单个公共构造方法对象
  - `Constructor<T> getDeclaredConstructor(Class<?>... parameterTypes)`：返回单个构造方法对象（包括私有）

- 利用Constructor创建对象

  - `T newInstance(Object...initargs)`：根据指定的构造方法创建对象

    ```java
    package fanshe;
    
    import java.lang.reflect.Constructor;
    import java.lang.reflect.InvocationTargetException;
    
    public class Demo1 {
    
    	public static void main(String[] args) throws ClassNotFoundException, InstantiationException, IllegalAccessException, IllegalArgumentException, InvocationTargetException, NoSuchMethodException, SecurityException {
    		// 获取字节码文件
    		Class clazz = Class.forName("fanshe.Student");
    		
    		// 获取构造方法
    		Constructor constructor = clazz.getConstructor(String.class, int.class);
    		
    		// 利用newInstance 创建对象
    		Student student = (Student) constructor.newInstance("张三", 11);
    		System.out.println(student);
    
    	}
    }
    ```

    > 在Class类中，有一个newInstance 方法，可以利用空参直接创建一个对象
    >
    > `Class clazz = Class.forName("fanshe.Student");`
    >
    > `Student stu = (Student)clazz.newInstance();`
    >
    > 不过这个方法现在已经过时了，了解即可

    ```java
    // 获取一个私有的构造方法并创建对象
    package fanshe;
    
    import java.lang.reflect.Constructor;
    import java.lang.reflect.InvocationTargetException;
    
    public class Demo2 {
    
    	public static void main(String[] args) throws ClassNotFoundException, InstantiationException, IllegalAccessException, IllegalArgumentException, InvocationTargetException, NoSuchMethodException, SecurityException {
    		// 获取字节码文件
    		Class clazz = Class.forName("fanshe.Student");
    		
    		// 获取构造方法
    		Constructor constructor = clazz.getConstructor(String.class, int.class);
            
    		// 被private修饰的成员，不能直接使用
            // 如果用反射强行获取并使用，需要临时取消访问检查
            constructor.setAccessible(true);
            
    		// 利用newInstance 创建对象
    		Student student = (Student) constructor.newInstance("张三", 11);
    		System.out.println(student);
    
    	}
    }
    ```

    > 在获取到的构造方法创建对象时，如果是public，可以直接创建对象
    >
    > 如果是非public的，需要临时取消检查，然后再创建对象`setAccessible(boolean)`（暴力反射）

- 反射获取成员变量

  - 步骤

    - 获得class对象

    - 获得Field对象

      | 方法名                                | 说明                                   |
      | ------------------------------------- | -------------------------------------- |
      | Field[] getFields()                   | 返回所有公共成员变量对象的数组         |
      | Field[] getDeclaredFields()           | 返回所有成员变量对象的数组（包括私有） |
      | Field[] getField(String name)         | 返回单个公共成员变量对象               |
      | Field[] getDeclaredField(String name) | 返回单个公共成员变量对象（包括私有）   |

    - 赋值或者获取值
      `void set(Object obj, Object value)`：给指定对象的成员变量赋值
      `Object get(Object obj)`：返回指定对象的Field的值

  - 代码实现

    ```java
    package fanshe;
    
    import java.lang.reflect.Field;
    
    public class Demo2 {
    
    	public static void main(String[] args) throws NoSuchFieldException, SecurityException, ClassNotFoundException, InstantiationException, IllegalAccessException {
    		// 获取class对象
    		Class clazz = Class.forName("fanshe.Student");
    		// 获取Field对象
    		Field field = clazz.getDeclaredField("name");
    		// 赋值
    			// 创建一个对象
    		Student stu = (Student)clazz.newInstance();
    			// 关闭访问检查（私有变量）
    		field.setAccessible(true);
    			// 赋值
    		field.set(stu, "张三");
    		System.out.println(stu);
    	}
    }
    ```

- 获取Method对象
  - 步骤

    - 获取class对象

    - 获取Method对象

      | 方法名                                                       | 说明                                                 |
      | ------------------------------------------------------------ | ---------------------------------------------------- |
      | Method[] getMethods()                                        | 返回所有公共成员方法对象的数组，包括继承的           |
      | Method[] getDeclaredMethods()                                | 返回所有成员方法对象的数组，不包括继承的，包括私有的 |
      | Method[] getMethod(String name, Class<?>...parameterTypes)   | 返回单个公共成员方法对象                             |
      | Method[] getDeclaredMethod(String name, Class<?>...parameterTypes) | 返回单个成员方法对象（包括私有）                     |

    - 运行方法
      `Object invoke(Object obj, Object...args)`：运行方法
      参数一：表示用obj对象调用该方法
      参数二：调用方法的传递的参数（如果没有就不写）
      返回值：方法的返回值（没有就不写）

  - 代码演示

    ```java
    package fanshe;
    
    import java.lang.reflect.InvocationTargetException;
    import java.lang.reflect.Method;
    
    public class Demo3 {
    	public static void main(String[] args) throws NoSuchMethodException, SecurityException, ClassNotFoundException, InstantiationException, IllegalAccessException, IllegalArgumentException, InvocationTargetException{
    		// 获取class对象
    		Class clazz = Class.forName("fanshe.Student");
    		// 获取Method对象
    		Method method = clazz.getDeclaredMethod("function", String.class, int.class);
    		// 创建对象
    		Student stu = (Student)clazz.newInstance();
    		// 运行
    		method.setAccessible(true);
    		method.invoke(stu, "张三",23);
    	}
    }
    ```


### xml

#### 概述

- 由万维网联盟（W3C）推出
  是Web领域最具权威和影响力的国际中立性技术标准机构
- 可扩展的标记语言XML(标准通用标记语言下的一个子集)
  标记语言：通过标签来描述数据的一门语言（标签也称为元素）
  可扩展：标签的名字是可以自己定义的
- 作用：
  - 用于进行存储数据和传输数据
  - 作为软件的配置文件

#### 规则

- 标签规则

  - 标签由一对尖括号和合法的标识符组成
  - 标签必须成对出现
  - 特殊标签可以不成对，但是必须要有结束标记
  - 标签中可以定义属性，属性和标签名空格隔开；属性值必须用引号引起来
  - 标签需要正确的嵌套

- 语法规则

  - 文件后缀名为：xml
  - 文档声明必须是第一行第一列
    `<?xml version = "1.0" encoding = "UTF-8" standalone = "yes"?>`
    version：该属性是==必须存在==的
    encoding：该属性==不是必须==的，声明打开当前xml文件的时候应该使用什么字符编码表
    standalone：该属性==不是必须==的，描述XML文件是否依赖其他的xml文件，取值为yes/no
  - 必须存在一个根标签，==有且仅有一个==
  - XML文件中可以定义注释信息
  - XML文件中可以存在特殊字符（\&lt;  \&gt;......）
  - XML文件中可以存在CDATA区
    `<![CDATA[...内容...]]>`

- 演示

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!--根标签-->
  <students>
      <!--第一个学生信息-->
  	<student id="1">
      	<name>张三</name>
          <age>23</age>
          <info>学生 &lt; &gt;信息</info>
          <!--CDATA区内的内容都会原样输出，大于号和小于号等不用使用特殊字符转义-->
          <message><![CDATA[内<>容]]></message>
      </student>
      <!--第二个学生信息-->
      <student id="2">
      	<name>李四</name>
          <age>24</age>
          <info></info>
      </student>
  </students>
  ```

#### 解析

- 解析就是从xml中获取到数据

- DOM(Document Object Model)文档对象模型：就是把文档的各个组成部分看做成对应的对象
  会把xml文件全部加载到内存。在内存中形成一个树形结构，再获取到对应的值

- 常见的解析工具

  - JAXP:SUN公司提供的一套XML的解析的API
  - JDOM：开源组织提供了一套XML的解析的API-jdom
  - DOM4J：开源组织提供了一套XML的解析的API-dom4j（全称：Dom For Java）
  - pull：主要应用在Android手机端解析XML

- DOM4J
  下载地址：https://dom4j.github.io/

  - 常用方法
    `SAXReader saxReader = new SAXReader();`：获取一个解析器对象
    `Document document = saxReader.read(new File("xml文件路径"))`：利用解析器把xml文件加载到内存中，并返回一个文档对象
    `Element rootElement = document.getRootElement()` ：获取到根标签
    `List list = rootElement.elements()` ：获取调用者所有的子标签，并加入到集合，最终返回这个集合
    `List list = rootElement.elements("标签名")` ：获取调用者所有的指定的子标签，会把这些子标签放到一个集合中并返回

    `Attribute attribute = element.attribute("属性名")` ：获取标签对应的属性
    `String id = attribute.getValue()`：获取对应属性的值
    `Element nameElement = element.element("标签名");`：获取调用者指定的子标签
    `String name = nameElement.getText()`：获取这个标签的标签体内容

- 代码

  ```java
  package MyXml;
  
  import java.io.File;
  import java.util.ArrayList;
  import java.util.List;
  
  import org.dom4j.Attribute;
  import org.dom4j.Document;
  import org.dom4j.DocumentException;
  import org.dom4j.Element;
  import org.dom4j.io.SAXReader;
  
  public class Demo {
  
  	public static void main(String[] args) throws DocumentException {
  		// 获取一个解析器对象
  		SAXReader saxReader = new SAXReader();
  		// 利用解析器把xml文件加载到内存中
  		Document document = saxReader.read(new File("src\\MyXml\\Students.xml"));
  		// 获取到根标签
  		Element rootElement = document.getRootElement();
  		// 获取子标签
  		List<Element> list = rootElement.elements("student");
  		// 遍历获取每个student信息
  		ArrayList<Student> s = new ArrayList();
  		for(Element element : list){
  			// 获取属性
  			Attribute attribute = element.attribute("id");
  			String id = attribute.getText();
  			// 获取name
  			Element nameElement = element.element("name");
  			String name = nameElement.getText();
  			// 获取age
  			Element ageElement = element.element("age");
  			int age = Integer.parseInt(ageElement.getText());
  			Student stu = new Student(id,name,age);
  			s.add(stu);
  		}
  		System.out.println(s);
  	}
  }
  ```

### DTD&schema

#### 约束

- 用来限定xml文件中可使用的标签以及属性
- 分类
  - DTD
  - schema

#### DTD约束

- 步骤

  - 创建一个文件，这个文件的后缀名为.dtd
  - 看xml文件中使用了哪些元素
    <!ELEMENT>可以定义元素：`<!ELEMENT persons>`
  - 判断元素是简单元素还是复杂元素
    - 简单元素：没有子元素`<!ELEMENT name (#PCDATA)>`
    - 复杂元素：有子元素的元素`<!ELEMENT person (name,age)>`
  - 引入DTD

- 引入DTD约束的三种方法

  - 引入本地dtd：`<!DOCTYPE 根标签名 SYSTEM 'DTD文件路径'>`
  - 在xml文件内部引入：`<!DOCTYPE 根标签名 [DTD文件内容]>`
  - 引入网络dtd：`<!DOCTYPE 根标签名 PUBLIC "dtd文件名称" "dtd文档的URL">`

- DTD语法规则

  - 定义一个元素：`<!ELEMENT 元素名 元素类型>`

    > 元素类型
    > **简单元素：**
    > EMPTY：表示标签体为空
    >
    > ANY：表示标签体可以为空也可以不为空
    >
    > PCDATA：表示该标签的内容部分为字符串
    >
    > **复杂元素：**
    > 直接写子元素名称
    > 多个子元素可以用","或者'|'隔开；
    > ","表示定义子元素的顺序
    > "|"表示子元素只能出现任意一个
    > （？表示零次或多次；"+"表示一次或多次；"*"表示零次或多次；如果不写默认表示出现一次）

  - 定义一个属性：`<!ATTLIST 元素名称 属性名称 属性类型 属性约束>`
    属性类型：CDATA类型（普通的字符串）
    属性约束

    > #REQUIRED：必需的
    > #IMPLIED：属性不是必需的
    > #FIXED value：属性值是固定的

#### schema约束

- schema和DTD的区别

  - schema约束文件也是一个xml文件，符合xml语法，后缀名为.xsd

  - 一个xml中可以引用多个schema约束文件，多个schema使用名称空间区分（名称空间类似于java包名）

  - dtd里面元素类型的取值比较单一常见的是PCDATA类型，但是在schema里面可以支持很多个数据类型

  - schema语法更加复杂

    > **schame文件用来约束一个xml文件，因为其自身也是一个xml文件，所以同时也被别的文件约束着**

- 步骤

  - 创建一个文件，这个文件后缀名为.xsd
  - 定义文档声明
  - schema文件的根标签为：`<schema>`
  - 在<schema>中定义属性：
    `xmlns=http://www.w3.org/2001/XMLSchema`（声明这个schema文件是一个约束文件，同时也被约束）
  - 在<schema>中定义属性：
    `targetNamespace=唯一的url地址`（指定当前这个schema文件的名称空间）
  - 在<schema>中定义属性：
    `elementFormDefault="qualified"`（表示当前schema文件是一个质量良好的文件）
  - 通过element定义元素
  - 判断当前元素是简单元素还是复杂元素

- 代码实现

  ```xml
  <? xml version="1.0" encoding="UTF-8" ?>
  <schema
  	xmlns="http://www.w3.org/2001/XMLSchema"
      targetNamespace="http://www.baidu.com/javase"
      elementFormDefault="qualified"
  >
  	<!--定义persons复杂元素-->
      <element name="persons">
          <complexType>		<!--复杂元素-->
              <sequence>		<!--里面元素必须按顺序-->
              	<!--定义person复杂元素-->
                  <element name="person">
                      <complexType>
                          <sequence>
                          	<!--定义name和age简单元素-->
                              <element name = "name" type = "string"></element>
                              <element name = "age" type = "int"></element>
                          </sequence>
                      </complexType>
                  </element>
              </sequence>
          </complexType>
      </element>
  </schema>
  ```

- 引入schema文件约束
  - 在根标签上定义属性
    `xmlns:xsi ="http://www.w3.org/2001/XMLSchema-instance"`（表示当前文件被别人约束）
  - 通过xmlns引入约束文件的名称空间
    `xmlns = "约束文件的名称空间"`
  - 给某一个xmlns属性添加一个标识，用于区分不同的名称空间
    格式为`xmlns:标识 = "名称空间地址"`
    标识是可以任意的，但是一般取值都是xsi
  - 通过`xsi:schemaLocation`指定名称空间所对应的约束文件路径
    格式为：`xsi:schemaLocation = "名称空间url 文件路径"`

- Schema定义属性
  - `<attribute name="id" type="string" use="required"></attribute>`
    use中两个选项：requried(必需的)、optional(可选的)

### 枚举&注解

- 用常量表示季节的弊端
  代码不够简洁
  不同类型的数据是通过名字区分的
  不安全，由于是数字类型，就有可能使用这几个值做一些运算操作；

> 为了间接的表示一些固定的值，Java提供了枚举

#### 枚举格式

- 枚举：是指将变量的值一一列出来，变量值只限于列举出来的值的范围内

- 格式

  ```java
  public enum s{
      枚举项1,枚举项2,枚举项3;
  }
  ```

  ```java
  // 定义一个枚举类，用来表示春、夏、秋、冬
  public enum Season{
      SPRING,SUMMER,AUTUMN,WINTER;
  }
  ```

#### 枚举特点

1. 所有枚举类都是Enum的子类
2. 可以通过"枚举类名.枚举项名称"去访问指定的枚举项
3. **每一个枚举项其实就是该枚举的一个对象**
4. 枚举也是一个类，也可以去定义成员变量
5. 枚举类的第一行上必须是枚举项，最后一个枚举项后的分号是可以省略的，但是如果枚举类有其他的东西，这个分号就不能省略。建议不要省略
6. 枚举类可以有构造器，但必须是private的，它默认的也是private的。
7. 枚举类也可以有抽象方法，但是枚举项必须重写该方法

```java
public enum Season{
    SPRING("春"){
       // 枚举类中有抽象方法，必须重写
        public void show(){
            System.out.println(this.name);
        }
    },
    SUMMER("夏"){
        public void show(){
            System.out.println(this.name);
        }
        
    },
    AUTUMN("秋"){
        public void show(){
            System.out.println(this.name);
        }
        
    },
    WINTER("冬"){
        public void show(){
            System.out.println(this.name);
        }
        
    };
    // 成员变量
    public String name;
    // 有参构造
    private Season(String name){
        this.name = name;
    }
    // 抽象方法
    public abstract void show();
}
```

#### 枚举的方法

| 方法名                                           | 说明                                 |
| ------------------------------------------------ | ------------------------------------ |
| String name()                                    | 获取枚举项的名称                     |
| int ordinal()                                    | 返回枚举项在枚举类中的索引值         |
| int compareTo(E o)                               | 比较两个枚举项，返回的是索引值的差值 |
| String toString()                                | 返回枚举常量的名称                   |
| static <T> T valueOf(Class<T> type, String name) | 获取指定枚举类中的指定名称的枚举值   |
| values()                                         | 获得所有的枚举项                     |

#### 注解

- 主要作用：对程序进行标注和解释

| 注解名                                      | 说明                   |
| ------------------------------------------- | ---------------------- |
| @Override                                   | 概述子类重写父类的方法 |
| @Deprecated                                 | 概述方法过时           |
| @SuppressWarnings                           | 压制警告               |
| @Retention(value = RetentionPolicy.RUNTIME) | 表示这个注解的存活时间 |

- 注释和注解
  注释：给程序员看
  注解：给编译器看(让虚拟机看到程序中的注解，注解代表程序的一些特殊功能)

- 自定义注解

  ```java
  public @interface 注解名称{
      public 属性类型 属性名 () default 默认值;		//这里只能是public，可省略
  }
  ```

  > 属性类型可以为基本数据类型、String、Class、注解、枚举以及以上类型的一维数组
  >
  > 在使用注解的时候如果注解里面的属性没有指定默认值，那么就需要手动给出注解属性的设置值

  >  特殊属性value：在使用注解时如果只给value赋值，那么可以直接设置

- `isAnnotationPresent(Class<? extends Annotation> annotationClass)`
  判断当前方法上是否有指定的注解
  参数：注解的字节码文件对象
  返回值：布尔结果     true存在；false不存在

#### 元注解

- 概述：就是描述注解的注解

| 元注解名    | 说明                                  |
| ----------- | ------------------------------------- |
| @Target     | 指定了注解能在哪里使用                |
| @Retention  | 可以理解为保留时间（生命周期）        |
| @Inherited  | 表示修饰的自定义注解可以被子类继承    |
| @Documented | 表示该自定义注解，会出现在API文档里面 |

> `@Target`：成员变量(ElementType.FIELD)，类(ElementType.TYPE)，成员方法(ElementType.METHOD)
>
> `@Retention`：不写默认只能存活在java文件(不能存活在class文件中)，括号写上`RetentionPolicy.RUNTIME`就可以存活到字节码中

### 单元测试&日志技术

- Junit概述：Junit是一个Java编程语言的单元测试工具。Junit是一个非常重要的测试工具

#### Junit特点

- 是一个开放源代码的测试工具
- 提供注解来识别测试方法
- 可以让编写代码更快，并提高质量
- 优雅简洁、简单
- 在一个条中显示进度，如果运行良好是==绿色==；运行失败为**红色**

#### 基本使用

- 将junit的jar包导入到工程中
- 编写测试方法，该测试方法必须是公共的无参数无返回值的非静态方法
- 在测试方法上使用@Test注解标注该方法是一个测试方法
- 选中测试方法右键通过junit运行该方法

#### 常用注解

| 注解    | 含义               |
| ------- | ------------------ |
| @Test   | 表示测试该方法     |
| @Before | 在测试的方法前运行 |
| @After  | 在测试的方法后运行 |

#### 日志技术

- 日志：程序中的日志可以用来记录程序在运行时的点点滴滴，并可以进行永久存储

- 区别

  |          | 输出语句                   | 日志技术                                 |
  | -------- | -------------------------- | ---------------------------------------- |
  | 取消日志 | 需要修改代码，灵活性比较差 | 不需要修改代码，灵活性比较好             |
  | 输出位置 | 只能是控制台               | 可以将日志信息写入到文件或者数据库中     |
  | 多线程   | 和业务代码处于一个线程中   | 多线程方式记录日志，不影响业务代码的性能 |

- 体系结构
  ![](E:\Typora\学习笔记\images\日志体系结构.png)
  
- Log4j
  是Apache的一个开源项目，通过Log4j，可以控制日志信息输送的===目的地是控制台、文件==等位置
  也可以控制每一条==日志输出格式==
  通过==定义==每一条日志信息的==级别==，能够更细致的控制日志的生成过程
  这些可以通过一个==配置文件==来灵活的进行配置，不需要修改应用的代码
  
- Log4j开发流程

  - 导入log4j的相关jar包

  - 编写log4j配置文件(log4j.properties/log4j.xml)

  - 在代码中获取日志的对象

    > log4j自己的api(不推荐使用)
    >
    > 弊端：如果以后要更换日志的实现类，那么下面的代码就要跟着改
    >
    > `private static final Logger LOGGER = Logger.getLogger(.class字节码文件);`

    > 使用slf4j里面的api来获取日志的对象
    >
    > 好处：如果更换日志的实现类，下面的代码不需要更改
    >
    > `private static final Logger LOGGER = LoggerFactory.getLogger(clss字节码文件)`

- 按照级别设置记录日志信息

- Log4j组成

  - Loggers(记录器)：日志的级别

    > 常用级别：
    > DEBUG		打印基本信息
    > INFO		打印重要信息
    > WARN		打印可能出现问题的信息
    > ERROR		出现错误的信息，不影响程序运行
    > FATAL	重大错误，程序可以停止
    > DEBUG<INFO<WARN<ERROE<FATAL
    >
    > Log4j有一个规则：只输出级别不低于设定级别的日志文件

  - Appenders(输出源)：日志要输出的地方，如控制台(Console)、文件(Files)等。
    `org.apache.log4j.ConsoleAppender`（控制台）
    `org.apache.log4j.FileAppender`（文件）

    ```properties
    log4j.appender.ca = org.apache.log4j.ConsoleAppender
    log4j.appender.ca.设置1 = 值1
    log4j.appender.ca.设置2 = 值2
    ...........
    ```

  - Layouts(布局)：日志输出的格式

    > 常用布局管理器：
    > `org.apache.log4j.PatternLayout`(可以灵活的指定布局模式)==【最常用】==
    > `org.apache.log4j.SimpleLayout`(包含日志信息的级别和信息字符串)
    > `org.apache.log4j.TTCCLayout`(包含日志产生的时间、线程、类别等信息)

    ```properties
    log4j.appender.ca.layout = org.apache.log4j.PatternLayou
    log4j.appender.ca.layout.设置1 = 值1
    log4j.appender.ca.layout.设置2 = 值2
    ...........
    ```

- 配置文件详解

  - 配置根Logger

    > 格式：`log4j.rootLogger = 日志级别, appenderName1, appenderName2, ...`
    > 日志级别：OFF FATAL ==ERROR WARN INFO DEBUG== ALL或者自定义的级别
    > appenderName1：就是指定日志信息要输出到哪里。可以同时指定多个输出目的地，用逗号隔开
    > 例如：`log4j.rootLogger = INFO, ca, fa`

  - 配置文件

    > ConsoleAppender常用的选项
    > ImmediateFlush = true		表示所有消息都会被立即输出，设置为false则不输出，默认为true
    > Target = System.err			默认值是System.out

    > FileAppender常用的选项
    > ImmediateFlush = true		表示所有消息都会立即被输出。设为false则不输出，默认值是true
    > Append = false		true表示将消息添加到指定文件中，原来的消息不覆盖
    > 								false则将消息覆盖指定的文件内容，默认值为true
    > File = D:/logs/logging.log4j		指定消息输出到logging.log4j文件中

  - 配置Layout

    > PatternLayout常用的选项
    > ConversionPattern=%m%n		设定以怎样的格式显示消息
    > 【格式化符号说明可以查看网上的资料做一个了解】

- Log4j应用
  - 使用步骤
    - 导入相关的依赖(jar)
    - 将资料中的properties配置文件复制到src目录下
    - 在代码中获取日志的对象
    - 按照级别设置记录日志信息

# JavaWeb

## Linux

## HTML+CSS+Nginx

## JavaWeb核心

## Mysql

## JDBC

## Mybatis

## JavaScript

## JQuery

## AJAX

## Vue+Element

## Redis

## Maven基础

## Web项目实战-黑马页面

# 主流框架

## Spring

## SpringMVC

## Maven高级

## Dubbo

## Zookeeper

# 医疗实战-传智健康



