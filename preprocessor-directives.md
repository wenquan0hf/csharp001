# C# - 预处理指令

预处理指令是一种给编译器的指令，用来在实际的编译开始之前预处理一些信息。

所有的预处理指令都以#开始，并且在一行预处理指令中，只有空白字符可以出现在指令之前。预处理指令没有声明，所以他们不需要以分号（；）结尾。


C# 编译器不具有独立的预处理机制；然而，指令执行的时候就像是只有这一条一样。在 C# 中，预处理指令被用来帮助条件编译。不像 C 或 C++ 的指令，他们不能创建宏。一个预处理指令必须是这一行代码中的唯一的指令。

## C# 中的预处理指令
下面的表格中列出了 C# 中可用的预处理指令：


| 预处理指令        | 描述           |
| ------------- |:-------------:|
| #define      | 定义了一串字符，称为符号。 |
| #undef      | 可以取消定义的符号。     |
| #if | 测试一个或多个表达式的结果是否为真。      |
| #else      | 用于创建复合条件指令，和#if一起使用。 |
| #elif      | 用于创建复合条件指令。      |
| #endif | 指出条件指令的结尾。      |
| #line      | 可以修改编译器的行号，选择性修改输出错误和警告的文件名|
| #error      | 从代码的特定位置生成误差      |
| #warning | 从代码的特定位置生成一级预警      |
| #region      | 当你使用Visual Studio 代码编译器时，你可以展开或折叠一部分代码块 |
| #engregion      | 它标志着#region 块的结束      |

## #define 指令

 # define 预处理指令是用来创建符号常量的。

应用 #define 可以定义一个符号，这个符号会作为一个表达式传递给 #if 指令，这个判断会得到 ture 的 结果。语法如下：

```

    #define symbol

```

下面的程序说明了这一点：

```

	#define PI 
	using System;
	namespace PreprocessorDAppl
	{
   		class Program
   		{
      		static void Main(string[] args)
      		{
         		#if (PI)
            	Console.WriteLine("PI is defined");
         		#else
            	Console.WriteLine("PI is not defined");
         		#endif
         		Console.ReadKey();
      		}
   		}
	}

```

编译执行上述代码，得到如下结果：

```

	PI is defined

```


## 条件指令

你可以使用 #if 指令创建一个条件指令。条件指令可以用来判断一个或多个符号是否为真。如果他们的结果为真，编译器就会执行 #if 和下一条指令间的所有代码。

条件指令的语法如下：

```

	#if symbol [operator symbol]...

```

当你想测试的符号是“ symbol ”这个名字的时候。你也可以使用 ture 和 false 或者提前使用反运算符操作这个符号。

**operator symbol**（运算符符号）是一种用于符号求值的运算符。运算符可以是下列之一：

* **== (相等)**
* **!= (不相等)**
* **&& (与)**
* **|| (或)**

你也可以通过括号使用组符号和组运算符。条件指令用于编译代码生成 debug 或者是编译特定配置时。一个条件指令以 #if 开头并且必须明确的以 #endif 指令结束。

下面的程序示范了条件指令的使用方法：

```
	
	#define DEBUG
	#define VC_V10
	using System;
	public class TestClass
	{
   		public static void Main()
   		{
      		#if (DEBUG && !VC_V10)
         		Console.WriteLine("DEBUG is defined");
      		#elif (!DEBUG && VC_V10)
         		Console.WriteLine("VC_V10 is defined");
      		#elif (DEBUG && VC_V10)
         		Console.WriteLine("DEBUG and VC_V10 are defined");
      		#else
         		Console.WriteLine("DEBUG and VC_V10 are not defined");
      		#endif
      		Console.ReadKey();
   		}
	}
```

编译执行上述代码，得到如下结果：

```

	DEBUG and VC_V10 are defined

```
