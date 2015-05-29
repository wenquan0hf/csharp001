# C\# 数组
数组存储一个大小固定的顺序集合中相同类型的元素。数组用于存储数据的集合，但我们通常认为数组是一个存储在连续的内存位置的相同类型的集合。  
相反，声明单个变量，如 number0, number1, ..., 和 number99，声明一个数组变量，如 numbers[0], numbers[1],…, 和 numbers[99] 表示单个变量。在数组的特定元素由一个索引进行访问。  
所有数组都由连续的内存位置构成。最低的地址对应于第一元素，最高地址为最后一个元素地址。  
![](images/arrays.jpg)

## 声明数组
要在 C# 中声明数组，可以使用下面的语法：
```
datatype[] arrayName;
```
这里，
-	*datatype 用于指定要被存储在数组中的元素的类型*
- *[ ] 指定数组的大小*
-	*arrayName 指定数组的名称*
例如，
```
double[] balance;
```
## 初始化数组
声明没有在存储器初始化的数组。当数组变量初始化时，您可以赋值给数组。  
数组是引用类型，所以需要使用 new 关键字来创建数组的一个实例。  
例如，
```
double[] balance = new double[10];
```
## 赋值数组
 
通过使用索引号，可以将值指派给单独的数组元素，比如：
```
double[] balance = new double[10];
balance[0] = 4500.0;
 ```
你可以在声明数组的同时给它赋值，如下：
```
double[] balance = { 2340.0, 4523.69, 3421.0};
```
你也可以创建和初始化一个数组，如下：
```
int [] marks = new int[5]  { 99,  98, 92, 97, 95};
```
你也可以省略数组的长度，如下：
```
int [] marks = new int[]  { 99,  98, 92, 97, 95};
```
你可以将一个数组变量赋给另一个目标。这种情况，两个数组都指向同一内存地址。
```
int [] marks = new int[]  { 99,  98, 92, 97, 95};
int[] score = marks;
```
当你创建一个数组时，C# 编译器初始化每个数组元素为数组类型的默认值。对于 int 数组的所有元素都初始化为 0。

## 访问数组元素
 
一个元素由索引数组名访问。这是通过放置在数组名后面的方括号里的元素索引完成的。例如：
```
double salary = balance[9];
```
以下是一个例子，将使用所有上述三个概念即声明，分配和访问数组：
```
using System;
namespace ArrayApplication
{
   class MyArray
   {
      static void Main(string[] args)
      {
         int []  n = new int[10]; /* n is an array of 10 integers */
         int i,j;

         /* initialize elements of array n */
         for ( i = 0; i < 10; i++ )
         {
            n[ i ] = i + 100;
         }
         
         /* output each array element's value */
         for (j = 0; j < 10; j++ )
         {
            Console.WriteLine("Element[{0}] = {1}", j, n[j]);
         }
         Console.ReadKey();
      }
   }
}
```
编译运行上述代码，得到以下结果：
 ```
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```
## 使用 foreach 循环
 
在前面的例子中，我们已经使用了一个 for 循环用于访问每个数组元素。还可以使用 foreach 语句来遍历数组。
```
using System;
namespace ArrayApplication
{
   class MyArray
   {
      static void Main(string[] args)
      {
         int []  n = new int[10]; /* n is an array of 10 integers */
         
         /* initialize elements of array n */
         for ( int i = 0; i < 10; i++ )
         {
            n[i] = i + 100;
         }
         
         /* output each array element's value */
         foreach (int j in n )
         {
            int i = j-100;
            Console.WriteLine("Element[{0}] = {1}", i, j);
            i++;
         }
         Console.ReadKey();
      }
   }
}
```
编译运行上述代码，得到以下结果：
```
Element[0] = 100
Element[1] = 101
Element[2] = 102
Element[3] = 103
Element[4] = 104
Element[5] = 105
Element[6] = 106
Element[7] = 107
Element[8] = 108
Element[9] = 109
```
## C\# 数组详解
 
数组在 C# 中是很重要的，应该需要很多更详细的解释。下列有关系到数组的几个重要概念，C# 程序员应当清楚：


|概念 | 	描述  |
| ------ | ------ |
|**[多维数组](http://www.tutorialspoint.com/csharp/csharp_multi_dimensional_arrays.htm)** | C# 支持多维数组。多维数组的最简单的形式是二维数组|
|**[锯齿状数组](http://www.tutorialspoint.com/csharp/csharp_jagged_arrays.htm)** | C# 支持多维数组，这是数组的数组 |
|**[通过数组到函数](http://www.tutorialspoint.com/csharp/csharp_passing_arrays_to_functions.htm)** |可以通过指定数组的名称没有索引传递给函数的指针数组 |
|**[参数数组](http://www.tutorialspoint.com/csharp/csharp_param_arrays.htm)** |这是用于使未知数量的参数传到函数 |
|**[Array类](http://www.tutorialspoint.com/csharp/csharp_array_class.htm )** |定义在系统命名空间中，它是基类所有的数组，并使用数组提供了各种属性和方法 |

