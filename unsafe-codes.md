# C\# 不安全代码
当代码段被 **unsafe** 修饰符标记时，C# 允许该代码段中的函数使用指针变量，故使用了**指针**变量的代码块又被称为**不安全代码**或非托管代码。
> 注意
>
> 若要在 [codingground](http://www.tutorialspoint.com/compile_csharp_online.php) 中执行本章的程序，请将 *Project >> Compile Options >> Compilation Command to* 中的编辑项设置为 mcs *.cs -out:main.exe -unsafe"


## 指针
指针是指其值为另一个变量的地址的变量，即内存位置的直接地址。如一般的变量或常量一样，在使用指针来存储其他变量的地址之前，必须先进行指针声明。

声明指针变量的一般形式为：

```
type *var-name;
```

以下为一些有效的指针声明示例：

```
int    *ip;    /* pointer to an integer */
double *dp;    /* pointer to a double */
float  *fp;    /* pointer to a float */
char   *ch     /* pointer to a character */
```

下述示例为在 C# 中使用了 unsafe 修饰符时指针的使用：

```
using System;
namespace UnsafeCodeApplication
{
   class Program
   {
      static unsafe void Main(string[] args)
      {
         int var = 20;
         int* p = &var;
         Console.WriteLine("Data is: {0} ",  var);
         Console.WriteLine("Address is: {0}",  (int)p);
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Data is: 20
Address is: 99215364
```

除了将整个方法声明为不安全代码之外，还可以只将部分代码声明为不安全代码，下面章节中的的示例说明了这点。

## 使用指针检索数据值
使用 **ToString()** 方法可以检索存储在指针变量所引用位置的数据。例如：

```
using System;
namespace UnsafeCodeApplication
{
   class Program
   {
      public static void Main()
      {
         unsafe
         {
            int var = 20;
            int* p = &var;
            Console.WriteLine("Data is: {0} " , var);
            Console.WriteLine("Data is: {0} " , p->ToString());
            Console.WriteLine("Address is: {0} " , (int)p);
         }
         
         Console.ReadKey();
      }
   }
}
```
编译执行上述代码，得到如下结果

```
Data is: 20
Data is: 20
Address is: 77128984
```

## 传递指针作为方法的参数
指针可以作为方法中的参数，例如：

```
using System;
namespace UnsafeCodeApplication
{
   class TestPointer
   {
      public unsafe void swap(int* p, int *q)
      {
         int temp = *p;
         *p = *q;
         *q = temp;
      }
      
      public unsafe static void Main()
      {
         TestPointer p = new TestPointer();
         int var1 = 10;
         int var2 = 20;
         int* x = &var1;
         int* y = &var2;
         
         Console.WriteLine("Before Swap: var1:{0}, var2: {1}", var1, var2);
         p.swap(x, y);

         Console.WriteLine("After Swap: var1:{0}, var2: {1}", var1, var2);
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Before Swap: var1: 10, var2: 20
After Swap: var1: 20, var2: 10
```

## 使用指针访问数组元素

在 C# 中，数组名称与一个指向与数组数据具有相同数据类型的指针是不同的变量类型。例如 int *p 和 int[] 是不同的类型。你可以对指针变量 p 进行加操作，因为它在内存中是不固定的，反之，数组的地址在内存中是固定的，因而无法对其直接进行加操作。

故如同 C 或 C++，这里同样需要使用一个指针变量来访问数组数据（[C 指针](http://www.tutorialspoint.com/cprogramming/c_pointers.htm)），并且需要使用 **fixed** 关键字来固定指针，示例如下：

```
using System;
namespace UnsafeCodeApplication
{
   class TestPointer
   {
      public unsafe static void Main()
      {
         int[]  list = {10, 100, 200};
         fixed(int *ptr = list)
         
         /* let us have array address in pointer */
         for ( int i = 0; i < 3; i++)
         {
            Console.WriteLine("Address of list[{0}]={1}",i,(int)(ptr + i));
            Console.WriteLine("Value of list[{0}]={1}", i, *(ptr + i));
         }
         
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Address of list[0] = 31627168
Value of list[0] = 10
Address of list[1] = 31627172
Value of list[1] = 100
Address of list[2] = 31627176
Value of list[2] = 200
```

## 编译不安全代码
必须切换命令行编译器到指定的 **/unsafe** 命令行才能进行不安全代码的编译。

例如，编译一个包含不安全代码的名为 prog1.cs 的程序，需要在命令行中输入如下命令：

```
csc /unsafe prog1.cs
```
在 Visual Studio IDE 环境中编译不安全代码，需要在项目属性中启用相关设置。

步骤如下：

* 双击资源管理器中的属性节点，打开**项目属性**。
* 点击 **Build** 标签页。
* 选择选项** "Allow unsafe code"**。
