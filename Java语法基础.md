# 1. Java 初识

****

## 1.1 第一个Java程序

****

一个 `Java` 程序可以认为是一系列对象的集合，而这些对象通过调用彼此的方法来协同工作。类似 `C/C++` 语言，需要一个函数（在面向对象中，这被称为方法）作为程序执行的入口点。

**基本概念**：

* **对象**：对象是类的一个实例，有状态和行为。
* **类**：类是一个模板，它描述一类对象的行为和状态。
* **方法**：方法就是行为，一个类可以有很多方法。逻辑运算、数据修改以及所有动作都是在方法中完成的。
* **实例变量**：每个对象都有独特的实例变量，对象的状态由这些实例变量的值决定。

**Java程序**：

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World"); 
    }
}
```

**关于public class HelloWorld**：

* `public class` 和 `class` 都是对类进行声明，用于定义类。
* 对于所有的类来说，类名的首字母应该大写。如果类名由若干单词组成，那么每个单词的首字母应该大写，例如  `MyFirstJavaClass` 。
* 使用 `public class` 时，必须保持类名与文件名一致，即 `public class HelloWorld` 的类名 `HelloWorld` 和文件名是一致的。
* 被 `public` 修饰的类可以被其他包访问，没有被 `public` 修饰的类可以访问 `public` 类，但不能被其他包访问。
* 每个文件中只能有不多于 $1$ 个 `public` 类（也可以没有）。

**关于public static void main(String[] args)**：

* `String args[]` 与  `String[] args`  都可以执行，但推荐使用 `String[] args`，这样可以避免歧义和误读。
* 既定主函数的格式，所有的 `Java` 程序由该方法开始执行。

**注意**：

* 对于大部分OJ平台，统一提供入口为 `public class Main`，之后代码示例将延用此标准。

****

## 1.2 注释

****

和 `C/C++` 一样，Java 使用 `//` 和 `/* */` 分别注释单行和多行。

**作用**：

* 可以用来解释程序的意思，还可以在让某段代码不执行（但是依然保留在源文件里）。
* 在代码中加一些说明和解释，方便自己或其他程序员程序员阅读代码。

**两种格式**：

1. **单行注释**：`// 描述信息` 
   - 通常放在一行代码的上方，或者一条语句的末尾，对该行代码说明。
2. **多行注释**： `/* 描述信息 */`
   - 通常放在一段代码的上方，对该段代码做整体说明。

**示例**：

```java
public class HelloWorld {
   /* 这是第一个Java程序
    * 它将输出 Hello World
    * 这是一个多行注释的示例
    */
    public static void main(String[] args){
       // 这是单行注释的示例
       /* 这个也是单行注释的示例 */
       System.out.println("Hello World"); 
    }
}
```

****

## 1.3 输入和输出

****

* 这里我们只介绍简单的输入和输出，关于抛异常等深入内容暂置后面的章节。

**A+B 示例**：

```java
import java.util.Scanner;  //导入Scanner包

public class Main{
    public static void main(String[] args){
        Scanner cin = new Scanner(System.in);
        int a = cin.nextInt();  //输入a
        int b = cin.nextInt();  //输入b
        
        System.out.println(a + b);  //输出a + b
        
    }
}
```

****

## 1.3.1 输入

****

**方式1**：

* 效率低，输入规模较小时使用。

```java
Scanner sc = new Scanner(System.in);
String str = sc.next();  // 读入下一个字符串
int x = sc.nextInt();  // 读入下一个整数
float y = sc.nextFloat();  // 读入下一个单精度浮点数
double z = sc.nextDouble();  // 读入下一个双精度浮点数
String line = sc.nextLine();  // 读入下一行
```

**方式2**：

* 效率较高，输入规模较大时使用。注意需要抛异常。

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String str = br.readLine();
        System.out.println(str);
    }
}
```

****

## 1.3.2 输出

****

**方式1**：

* 效率低，输出规模较小时使用。

```java
System.out.println(123);  // 输出整数 + 换行
System.out.println("Hello World");  // 输出字符串 + 换行
System.out.print(123);  // 输出整数
System.out.print("lys is dog\n");  // 输出字符串
System.out.printf("%04d %.2f\n", 4, 123.456D);  // 格式化输出，float与double都用%f输出
```

**方式2**：

* 效率较高，输出规模较大时使用。注意需要抛异常。

```java
import java.io.BufferedWriter;
import java.io.OutputStreamWriter;

public class Main {
    public static void main(String[] args) throws Exception {
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        bw.write("Hello World\n");
        bw.flush();  // 需要手动刷新缓冲区
    }
}
```

****

# 2. 数据类型

****

## 2.1 变量

****

**作用**：

- 给一段指定的内存空间起名，方便操作这段内存。
- 变量只是一个声明，声明存储对应的数据类型。

**语法**：

- `数据类型 变量名;`
- `数据类型 变量名 = 初始值;`

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int a = 5;
        int b, c = a, d = 10 / 2;
    }
}
```

****

## 2.2 内置数据类型

****

`Java` 语言提供了八种基本类型。六种数字类型（四个整数型，两个浮点型），一种字符类型，还有一种布尔型。

|  类型名   |    意义    | 字节数 |
| :-------: | :--------: | :----: |
|  `byte`   |  字节类型  |   1    |
|  `short`  |   短整型   |   2    |
|   `int`   |    整型    |   4    |
|  `long`   |   长整型   |   8    |
|  `float`  | 单精度浮点 |   4    |
| `double`  | 双精度浮点 |   8    |
| `boolean` |  布尔类型  |   1    |
|  `char`   |   字符型   |   2    |

****

**byte：**

- `byte` 数据类型是 $8$ 位、有符号的，以二进制补码表示的整数。
- 范围： $-128(-2^7)\sim 127(2^7-1)$。
- 默认值是 $0$。
- `byte` 类型用在大型数组中节约空间，主要代替整数，因为 `byte` 变量占用的空间只有 `int` 类型的四分之一。

**short：**

- `short` 数据类型是 $16$ 位、有符号的以二进制补码表示的整数。
- 范围： $-32768(-2^{P15})\sim 32767(2^{15} - 1)$。
- 默认值是 $0$；

**int：**

- `int` 数据类型是 $32$ 位、有符号的以二进制补码表示的整数。
- 范围： $-2,147,483,648(-2^{31})\sim 2,147,483,647(2^{31} - 1)$。
- 默认值是 $0$。
- 一般地整型变量默认为 `int` 类型。

**long：**

- `long` 数据类型是 $64$ 位、有符号的以二进制补码表示的整数。
- 最小值是 $-9,223,372,036,854,775,808(-2^{63})\sim 9,223,372,036,854,775,807（2^{63} -1)$。
- 默认值是 $0L$。
- 这种类型主要使用在需要比较大整数的系统上。
- "L"理论上不分大小写，但是若写成"l"容易与数字"1"混淆，不容易分辩。所以最好大写。

**float：**

- `float` 数据类型是单精度、$32$ 位、符合 `IEEE 754标准` 的浮点数。
- 默认值是 $0.0f$。
- 浮点数不能用来表示精确的值。
- `float` 在储存大型浮点数组的时候可节省内存空间。

**double：**

- `double` 数据类型是双精度、$64$ 位、符合 `IEEE 754标准`的浮点数。
- 默认值是 $0.0d$。
- `double` 类型同样不能表示精确的值。
- 浮点数的默认类型为 `double` 类型。

**boolean：**

- `boolean` 数据类型表示一位的信息。
- 只有两个取值：`true` 和 `false`。
- 默认值是 $false$。
- 这种类型只作为一种标志来记录 `true/false` 情况。

**char：**

- `char` 类型是一个单一的 $16$ 位 `Unicode` 字符。
- 范围： `\u0000(十进制等效值为 0) ~ \uffff(即为 65535)`。
- `char` 数据类型可以储存任何字符。

**字符串类型**：

*  字符串类型 `String` 是 `Java` 一个内置的类。`String` 表示字符串类型，属于 **引用数据类型**，不属于基本数据类型。
* 关于此内容详见后续章节。

**对应格式化输出**：

| 符号 |   意义   |
| :--: | :------: |
| `%d` | 整数类型 |
| `%f` | 浮点类型 |
| `%c` | 字符类型 |

****

## 2.3 特殊转义字符

****

`Java` 语言支持一些特殊的转义字符序列。

|   符号   |          字符含义          |
| :------: | :------------------------: |
|   `\n`   |        换行 (0x0a)         |
|   `\r`   |        回车 (0x0d)         |
|   `\f`   |        换页符(0x0c)        |
|   `\b`   |        退格 (0x08)         |
|   `\0`   |        空字符 (0x0)        |
|   `\s`   |        空格 (0x20)         |
|   `\t`   |           制表符           |
|   `\"`   |           双引号           |
|   `\'`   |           单引号           |
|   `\\`   |           反斜杠           |
|  `\ddd`  |      八进制字符 (ddd)      |
| `\uxxxx` | 16进制`Unicode`字符 (xxxx) |

****

## 2.4 常量

****

**作用**：

- 使用 `final` 修饰，用于记录程序中不可更改的数据。

**语法**：

- `final 数据类型 常量名 = 初始化值;`

**注意**：

- 常量是固定值，在程序执行期间不会改变。
- 常量的值在定义后不能被修改，修改则会报错。

****

## 2.5 类型转换

****

## 2.5.1 自动类型转换

****

**解释**：

*  整型、实型（常量）、字符型数据可以混合运算。运算中，不同类型的数据先转化为同一类型，然后进行运算。

**规则**：

*  转换从低级到高级。

```java
低  ----------------------------------------->  高
byte, short, char —> int —> long —> float —> double 
```

-  不能对 `boolean` 类型进行类型转换。

-  不能把对象类型转换成不相关类的对象。

-  在把容量大的类型转换为容量小的类型时必须使用强制类型转换。

-  转换过程中可能导致溢出或损失精度，例如：

  ```java
  int i =128;   
  byte b = (byte)i;
  ```

  因为 `byte` 类型是 $8$ 位，最大值为 $127$，所以当 `int` 强制转换为 `byte` 类型时，值 $128$ 时候就会导致溢出。

-  浮点数到整数的转换是通过舍弃小数得到，而不是四舍五入，例如：

  ```java
  (int)23.7 == 23;        
  (int)-45.89f == -45
  ```

**条件**：

*  必须满足转换前的数据类型的位数要低于转换后的数据类型。
* 例如：`short` 数据类型的位数为 $16$ 位，就可以自动转换位数为 $32$ 的 `int` 类型，同样 `float` 数据类型的位数为 $32$，可以自动转换为 $64$ 位的 `double` 类型。

**示例**

```java
public class Main{
        public static void main(String[] args){
            char c1='a';//定义一个char类型
            int i1 = c1;//char自动类型转换为int
            System.out.println("char自动类型转换为int后的值等于"+i1);
            char c2 = 'A';//定义一个char类型
            int i2 = c2+1;//char 类型和 int 类型计算
            System.out.println("char类型和int计算后的值等于"+i2);
        }
}
```

****

## 2.5.2 强制类型转换

****

**条件**：

*  转换的数据类型必须是兼容的。

**格式**：

* `(type)value type` 是要强制类型转换后的数据类型。

**示例**：

```java
public class Main{
    public static void main(String[] args){
        int i1 = 123;
        byte b = (byte)i1;//强制类型转换为byte
        System.out.println("int强制类型转换为byte后的值等于"+b);
    }
}
```

**隐含强制类型转换**

- 整数的默认类型是 `int`。
- 小数默认是 `double` 类型浮点型，在定义 `float` 类型时必须在数字后面跟上 `F` 或者 `f`。
- 例如：`double x = 12, y = 4 * 3.3;`

****

# 3. 运算符

****

## 3.1 算数运算符

****

**作用**：

* 用于处理四则运算 。

算术运算符包括以下符号：

| **运算符** | **术语**     | **示例**        | **结果**      |
| ---------- | ------------ | --------------- | ------------- |
| `+`        | 正号         | +3              | 3             |
| `-`        | 负号         | -3              | -3            |
| `+`        | 加           | 10 + 5          | 15            |
| `-`        | 减           | 10 - 5          | 5             |
| `*`        | 乘           | 10 * 5          | 50            |
| `/`        | 除           | 10 / 5          | 2             |
| `%`        | 取模(取余数) | 10 % 3          | 1             |
| `++`       | 前置递增     | a = 2; b = ++a; | a = 3; b = 3; |
| `++`       | 后置递增     | a = 2; b = a++; | a = 3; b = 2; |
| `--`       | 前置递减     | a = 2; b = --a; | a = 1; b = 1; |
| `--`       | 后置递减     | a = 2; b = a--; | a = 1; b = 2; |

**注意**：

* 在除法运算中，除数不能为 $0$。
* 只有整型变量可以进行取模运算。
* 前置递增先对变量进行 `++`，再计算表达式，后置递增相反。

****

## 3.2 赋值运算符

****

**作用**：

* 用于将表达式的值赋给变量。

赋值运算符包括以下几个符号：

| **运算符** | **术语** | **示例**       | **结果**      |
| ---------- | -------- | -------------- | ------------- |
| `=`        | 赋值     | a = 2; b = 3;  | a = 2; b = 3; |
| `+=`       | 加等于   | a = 0; a += 2; | a = 2;        |
| `-=`       | 减等于   | a = 5; a -= 3; | a = 2;        |
| `*=`       | 乘等于   | a = 2; a *= 2; | a = 4;        |
| `/=`       | 除等于   | a = 4; a /= 2; | a = 2;        |
| `%=`       | 模等于   | a = 3; a %= 2; | a = 1;        |

> 对于复合赋值运算符 `+=` ：例如 `a = 0; a += 2;`， 等价为 `a = 0; a = a + 2` ，结果 `a = 2`，其余复合赋值运算符的运算同理。

****

## 3.3 比较运算符

****

**作用：**

* 用于表达式的比较，并返回一个真值或假值。

比较运算符有以下符号：

| **运算符** | **术语** | **示例** | **结果** |
| ---------- | -------- | -------- | -------- |
| `==`       | 相等于   | 4 == 3   | 0        |
| `!=`       | 不等于   | 4 != 3   | 1        |
| `<`        | 小于     | 4 < 3    | 0        |
| `>`        | 大于     | 4 > 3    | 1        |
| `<=`       | 小于等于 | 4 <= 3   | 0        |
| `>=`       | 大于等于 | 4 >= 1   | 1        |

**注意**：

* 要将等于运算符 `==` 和赋值运算符 `=` 区分开来，这在判断语句中尤为重要。
* 例如：`if (op = 1)` 与 `if (op == 1)` 看起来类似，但实际功能却相差甚远。第一条语句是在对 op 进行赋值，若赋值为非 0 时为真值，表达式的条件始终是满足的，无法达到判断的作用；而第二条语句才是对 `op` 的值进行判断。

****

## 3.4 逻辑运算符

****

**作用**：

* 用于根据表达式的值返回真值或假值。

逻辑运算符有以下符号：

| **运算符** | **术语** | **示例** | **结果**                                                 |
| ---------- | -------- | -------- | -------------------------------------------------------- |
| `!`        | 非       | !a       | 如果a为假，则!a为真；  如果a为真，则!a为假。             |
| `&&`       | 与       | a && b   | 如果a和b都为真，则结果为真，否则为假。                   |
| `||`       | 或       | a \|\| b | 如果a和b有一个为真，则结果为真，二者都为假时，结果为假。 |

****

## 3.5 位运算符

****

**作用**

* 位运算就是基于整数的二进制表示进行的运算。
* 由于计算机内部就是以二进制来存储数据，位运算是相当快的。

**运算符及运算规则**：

| 运算 | 运算符 | 数学符号              | 解释                                           |
| ---- | ------ | --------------------- | ---------------------------------------------- |
| 与   | `&`    | $\&$                  | 只有两个对应位都为 $1$ 时才为 $1$              |
| 或   | `|`    | [latex] \mid [/latex] | 只要两个对应位中有一个为 $1$ 时就为 $1$        |
| 取反 | `~`    | $\sim$                | 按位取反，即对应的 $0$ 变为 $1$， $1$ 变为 $0$ |
| 异或 | `^`    | $\oplus$              | 只有两个对应位不同时才为 $1$                   |

```java
&  //与运算
0 & 0 = 0 ;
0 & 1 = 0 ;
1 & 0 = 0 ;
1 & 1 = 1 ;

|  //或运算
0 | 0 = 0 ;
0 | 1 = 1 ;
1 | 0 = 1 ;
1 | 1 = 1 ;

~  //取反运算
~ 0 = 1 ;
~ 1 = 0 ;

^  //异或运算
0 ^ 0 = 0 ;
0 ^ 1 = 1 ;
1 ^ 0 = 1 ;
1 ^ 1 = 0 ;

>> //右移运算
n >> k  //表示 n / 2^k 
    
<<  //左移运算
n << k  //表示 n * 2*k

```

**常用模板**

```java
//求x的第k位数字
x >> k & 1 ;

//求x的最后一位1
x & -x ;
```

****

## 3.6  逗号运算符

****

**作用**：

* 逗号运算符 `,` 可将多个表达式分隔开来，被分隔开的表达式按从左至右的顺序依次计算，整个表达式的值是最后的表达式的值。

**注意**：

* 逗号表达式的优先级在所有运算符中的优先级是**最低**的，即再进行多个表达式运算时，在所有其他运算符运算完毕后才执行逗号运算符的运算。

****

## 3.7 运算符优先级

****

**作用**：

* 不同的运算符在表达式中的优先级不同，会使得表达式按一定的运算规则进行运算，使得运算不发生歧义。

**优先级对照**：

取自[菜鸟教程](https://www.runoob.com/java/java-operators.html)

![](L:\JAVA\Java语法基础\图片\运算符优先级.png)

****

# 4. 程序流程结构

****

**和 C/C++ 一样， Java 也支持最基本的三种程序运行结构**：

* 顺序结构：程序按顺序执行，不发生跳转。
* 选择结构：依据条件是否满足，有选择的执行相应功能。
* 循环结构：依据条件是否满足，循环多次执行某段代码。

****

## 4.1 选择结构

****

## 4.1.1 if语句

****

**作用**：

* 执行满足条件的语句。

**语法**：

**基本 if 语句**：

```java
if(条件表达式){
    //语句
}
```

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int a = 10, b = 1;
        if(a > b) System.out.println("a is bigger to b");
    }
}
```

**if...else 语句**：

```java
if(条件表达式){
	//语句1
}
else{
	//语句2
}
```

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int a = 10, b = 100;
        if(a > b) System.out.println("a is bigger to b");
        else System.out.println("a is smaller to b");
    }
}
```

**else if 语句**：

```java
if(条件表达式1){
		//语句1
	}
	else if(条件表达式2){
		//语句2
	}
	else{
		//语句3
	}
```

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int a = 100, b = 100;
        if(a > b) System.out.println("a is bigger to b");
        else if(a == b) System.out.println("a is equal to b");
        else System.out.println("a is smaller to b");
    }
}
```

**嵌套 if 语句**：

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int a = 10, b = 100;
        if(a > b) System.out.println("a is bigger to b");
        else {
            if(a == b) System.out.println("a is equal to b");
            else System.out.println("a is smaller to b");
        }
    }
}
```

****

## 4.1.2 三目运算符

****

**作用**：

*  通过三目运算符实现简单的判断。

**语法**：

* `表达式1 ? 表达式2 ：表达式3;`

**解释：**

* 如果表达式 $1$ 的值为真，执行表达式 $2$，并返回表达式 $2$ 的结果。
* 如果表达式 $1$ 的值为假，执行表达式 $3$，并返回表达式 $3$ 的结果。

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int a = 100;
        int c = a > 10 ? -1 : a;  // 三目运算
        System.out.println(c);
    }
}
```

****

## 4.1.3 switch语句

****

**作用**：

* 执行多条件分支语句。

**语法：**

```java
switch(条件表达式){

	case 结果1：执行语句1; break;

	case 结果2：执行语句2; break;

	...

	default: 执行语句n; break;

}
```

**注意**：

* `switch` 语句执行时，先求出选择句的值，然后根据选择句的值选择相应的标签，从标签处开始执行。
* 其中，选择句必须是一个整数类型表达式，而标签都必须是整数类型的常量。
* `switch` 语句中还要根据需求加入 `break` 语句进行中断，否则在对应的 `case` 被选择之后接下来的所有 `case` 里的语句和 `default` 里的语句都会被运行。
* 当无对应的 `case` 条件时，会统一执行 `default` 的语句。

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int score = 100;
        switch (score){
            case 100:
            case 90:
                System.out.println("典");
                break;
            case 80:
            case 70:
                System.out.println("一般");
                break;
            default:
                System.out.println("烂片");
                break;
        }
    }
}
```

****

## 4.2 循环结构

****

## 4.2.1 while循环语句

****

**作用**：

* 满足循环条件，执行循环语句。

**语法**：

```java
while(条件表达式){
	//语句
}
```

**解释**：

* 先判断循条件表达式，只要循环条件的结果为真，就执行循环语句。
* ![](https://lys2021.com/wp-content/uploads/2022/08/循环w.png)

**注意**：

* 在执行循环语句时候，程序必须提供跳出循环的出口，否则出现死循环。

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int i = 0;
        while(i < 10){
            System.out.println(i);
            i ++;  // 每次循环 i 自增 1
        }
    }
}
```

****

## 4.2.2 do...while循环语句

****

**作用**： 

* 满足循环条件，执行循环语句。

**语法**：

```java
do{
    //语句
}while(条件表达式);
```

**解释**：

* 先执行一次语句，再判断条件表达式，只要条件表达式的结果为真，就执行循环语句。
* ![](https://lys2021.com/wp-content/uploads/2022/08/循环dw.png)

**注意：**

* 与 `while` 的区别在于 `do...while` 会先执行一次循环语句，再判断循环条件。

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        int i = -1;
        do{  // 先执行一次循环体内的内容
            System.out.println(i);
            i ++;
        }while (i > 0);  // 再判断循环的条件
        System.out.println(i);
    }
}
```

****

## 4.2.3 for循环语句

****

**作用**： 

* 先判断条件表达式，满足循环条件，执行循环语句。

**语法**：

```java
for(初始化条件; 判断条件; 更新){
	//语句
}
```

**注意**：

* `for` 循环中的表达式，要用分号进行分隔。
* `for` 语句的三个部分中，任何一个部分都可以省略。
* 其中，若省略了判断条件，相当于判断条件永远为真。

**解释**：

* 只要循环条件的结果为真，就执行循环语句。
* ![](https://lys2021.com/wp-content/uploads/2022/08/循环图.png)

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        for(int i = 0; i < 10; i ++){
            System.out.println(i);
        }
    }
}
```

****

## 4.2.4 嵌套循环

****

**作用**： 

* 在循环体中再嵌套一层循环，解决一些实际问题。

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        for(int i = 0; i < 10; i ++){
            for(int j = 0; j < i; j ++){  // 当 j < i 时
                System.out.print(j + " ");  // 输出 j
            }
            System.out.println();
        }
    }
}
```

****

## 4.3 跳转语句

****

## 4.3.1 break语句

****

**作用**： 

* 出现在`switch`条件语句中，作用是终止`case`并跳出`switch`。
* 出现在循环语句中，作用是跳出当前的循环语句。
* 出现在嵌套循环中，跳出最近的内层循环语句。

**示例1**：

```java
public class Main {
    public static void main(String[] args) {
        int n = 10;
        for(int i = 0; i <= n; i ++){
            if(i < 5) System.out.print(i + " ");  // i < 5 时跳出循环
            else break;
        }
    }
}
```

**示例2**：

```java
public class Main {
    public static void main(String[] args) {
        for(int i = 0; i < 10; i ++){
            for(int j = 0; j < 10; j ++){
                if(j > i) break;  // 当 j > i 时跳出该层循环
                else System.out.print(j + " ");
            }
            System.out.println();
        }
    }
}
```

****

## 4.3.2 continue语句

****

**作用：**

* 在循环语句中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环。

**注意**：

* `continue` 并没有使整个循环终止，而 `break` 会跳出循环。

**示例**：

```java
public class Main {
    public static void main(String[] args) {
        for(int i = 0; i < 10; i ++){
            if(i % 2 == 0) continue;  // 当 i 为偶数时跳过
            else System.out.println(i);
        }
    }
}
```

****

# 









