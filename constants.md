# C\#-常量和文字

常数是指该程序可能无法在其执行期间改变的固定值。这些固定值也被称为文字。常量可以是任意的基本数据类型，如整型常量，浮点常量，字符常量或字符串。还有的也可以是枚举常量。

常量就像是普通的变量，只是它们的值不能在定义后进行修改。

## 整数常量

一个整数常量可以是十进制，八进制，或十六进制常数。前缀指定基或基数：0x 或 0X 为十六进制，0表示八进制，十进制没有前缀标识。

一个整数常量也可以有一个后缀为 U 和 L 的组合，针对无符号型和长整型。后缀可以是大写或小写，并且可以以任意顺序。

这里是整数常量的一些例子：
```
212         /* Legal */
215u        /* Legal */
0xFeeL      /* Legal */
078         /* Illegal: 8 is not an octal digit */
032UU       /* Illegal: cannot repeat a suffix */
```

以下是不同类型的整型常量的其他例子：
```
85         /* decimal */
0213       /* octal */
0x4b       /* hexadecimal */
30         /* int */
30u        /* unsigned int */
30l        /* long */
30ul       /* unsigned long */
```

## 浮点常量

浮点常量具有一个整数部分，一个小数点，一个小数部分，和一个指数部分。你可以用十进制形式或指数形式来表示浮点常量。

下面是浮点常量的一些例子：
```
3.14159       /* Legal */
314159E-5L    /* Legal */
510E          /* Illegal: incomplete exponent */
210f          /* Illegal: no decimal or exponent */
.e55          /* Illegal: missing integer or fraction */
```

当采用十进制形式表示时，必须包括小数点、指数，或两者兼有；当采用指数形式表示时，必须包括整数部分、小数部分，或者两者同时存在。带符号的指数，通过 e 或 E 介绍.


## 字符常量

字符常量用单引号，例如，'x'，并可以存储在 char 类型的简单变量。字符常量可以是普通的字符（例如，'x'），转义序列（如“\t'），或通用字符（例如，'\u02C0'）。

在 C# 中有一些字符，当前面加一个反斜杠时会有特殊的含义，它们被用来表示类似的换行符（\n）或制表符（\t）。在这里，有一些这样的转义序列代码的列表：

| 转义序列 | 含义 |
| --- | --- |
|\\|\ 字符|
|\'|' 字符|
|\"|" 字符|
|\?|? 字符|
|\a|警报或铃|
|\b|退格|
|\f|换页|
|\n|换行符|
|\r|回车|
|\t|水平制表|
|\v|垂直制表|
|\ooo|一到三位数字的八进制数|
|\xhh|一个或多个数字的十六进制数|



以下的例子来说明一些转义字符序列：
```
using System;
namespace EscapeChar 
{
   class Program
   {
      static void Main(string[] args)
      {
         Console.WriteLine("Hello\tWorld\n\n");
         Console.ReadLine();
      }
   }
}
```

编译执行上述代码，得到如下结果：
```
Hello   World
```

## 字符串常量

字符串文字或常量用双引号“”或@“”。一个字符串包含的字符类似于字符常量：普通字符，转义序列和通用字符。

你可以使用字符串将一长列拆分为多行，使用空格拆分各部分。
```
"hello, dear"
"hello, \
dear"
"hello, " "d" "ear"
@"hello dear"
```

## 定义常量

常量使用const关键字定义。用于定义一个常数的语法是：
```
const <data_type> <constant_name> = value;
```

下面的程序示范了如何在你的程序中定义和使用常量：
```
using System;
namespace DeclaringConstants
{
    class Program
    {
        static void Main(string[] args)
        {
            const double pi = 3.14159;   
            
            // constant declaration 
            double r;
            Console.WriteLine("Enter Radius: ");
            r = Convert.ToDouble(Console.ReadLine());
            double areaCircle = pi * r * r;
            Console.WriteLine("Radius: {0}, Area: {1}", r, areaCircle);
            Console.ReadLine();
        }
    }
}
```

编译执行上述代码，得到如下结果：
```
Enter Radius: 
3
Radius: 3, Area: 28.27431
```


































