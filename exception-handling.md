# C# - 异常处理

异常是程序执行过程中产生的问题。C# 异常是对程序运行过程中出现的额外情况的一种反馈，例如除数为零时。

异常提供了一种将控制权从程序的一个部分转移到另一个部分的方式。C# 异常处理有四个关键词：**try**，**catch**，**finally**，**throw**。

* **try**：try 块标识代码块的哪些特定的异常将被激活。它的后面是一个或多个catch块。
* **catch**：一个用于捕获异常的程序段，将 catch 放在你希望能处理这个异常的地方。“catch”这个关键字标志着异常的捕获。
* **finally**：finally 保证了无论是否有异常抛出，此代码段中的程序都会被执行。例如，如果你打开了一个文件，那么不管是否发生了异常，文件都需要关闭。
* **throw**：当出现问题时，程序会抛出异常。这项工作是通过使用 throw 来实现的。

## 语法

假设一个代码块产生了一个异常，通过使用 try 和 catch 的组合可以捕获这个异常。一个 try/catch 代码块需要放置在可能会产生异常的代码段周围。try/catch 代码段就像是保护代码，它的使用语法如下：

```

	try
	{
  		// statements causing exception
	}
	catch( ExceptionName e1 )
	{
   		// error handling code
	}
	catch( ExceptionName e2 )
	{
   		// error handling code
	}
	catch( ExceptionName eN )
	{
   		// error handling code
	}
	finally
	{
   		// statements to be executed
	}
```

当你的 try 语句块可能会抛出多种异常时，你可以列出多种的 catch 语句，以便捕获不同种类的异常。

## C#中的异常类

C# 异常由类表示。在 C# 中的异常类主要是直接或间接地来源于 System.Exception 类。有些从 System.Exception 类派生的异常类，它们是 System.ApplicationException 和 System.SystemException 类。

System.ApplicationException 类支持由应用程序生成的异常。因此，由程序员定义的异常应该源于这个类。

System.SystemException 类是所有预定义的系统异常的基类。

下表提供了一些从Sytem.SystemException类派生的预定义的异常类：

| Exception类        | 描述           |
| ------------- |:-------------:|
| System.IO.IOException      | 处理 I/O 错误 |
| System.IndexOutOfRangeException      | 处理的方法是指当一个数组索引超出范围的错误产生     |
| System.ArrayTypeMismatchException | 处理时，类型不匹配的数组类型产生的错误      |
| System.NullReferenceException      | 处理从取消引用一个空对象产生的错误 |
| System.DivideByZeroException      | 处理来自将一个除零而产生的错误      |
| System.InvalidCastException | 处理类型转换过程中产生的错误      |
| System.OutOfMemoryException     | 处理来自可用内存不足产生的错误|
| System.StackOverflowException      | 处理从堆栈溢出产生的错误     |


## 处理异常

C# 为在 try catch 语句块中处理异常提供了一种结构化的解决方案。这种方法可以使核心代码段和异常处理部分分离开。

这些异常处理代码段是通过使用 try，catch，finally 关键字实现的。下面是一个除数为零的异常处理情况：

```

	using System;
	namespace ErrorHandlingApplication
	{
   		class DivNumbers
   		{
      		int result;
      		DivNumbers()
      		{
         		result = 0;
      		}
      		public void division(int num1, int num2)
      		{
         		try
         		{
            		result = num1 / num2;
         		}
         		catch (DivideByZeroException e)
         		{
            		Console.WriteLine("Exception caught: {0}", e);
         		}
         		finally
         		{
            		.WriteLine("Result: {0}", result);
         		}
      		}
      		static void Main(string[] args)
      		{
      	   		DivNumbers d = new DivNumbers();
         		d.division(25, 0);
         		Console.ReadKey();
      		}
   		}
	}
```

编译执行上述代码，得到如下结果：

```

	Exception caught: System.DivideByZeroException: Attempted to divide by zero. 
	at ...
	Result: 0
```

## 创建自定义异常

你也可以定义你自己的异常。自定义异常类继承自 ApplicationException 类。示范如下：

```

	using System;
	namespace UserDefinedException
	{
   		class TestTemperature
   		{
      		static void Main(string[] args)
      		{
         		Temperature temp = new Temperature();
         		try
         		{
            		temp.showTemp();
         		}
         		catch(TempIsZeroException e)
         		{
            		Console.WriteLine("TempIsZeroException: {0}", e.Message);
         		}
         		Console.ReadKey();
      		}
   		}
	}

	public class TempIsZeroException: ApplicationException
	{
   		public TempIsZeroException(string message): base(message)
   		{
   		}
	}

	public class Temperature
	{
   		int temperature = 0;
   		public void showTemp()
   		{
      		if(temperature == 0)
      		{
         		throw (new TempIsZeroException("Zero Temperature found"));
      		}
      		else
      		{
         		Console.WriteLine("Temperature: {0}", temperature);
     	 	}
   		}
	}
```

编译执行上述代码，得到如下结果：

```

	TempIsZeroException: Zero Temperature found

```

## 抛出对象

如果某个对象是直接或间接地继承自 System.Exception 类，你可以抛出这个对象。你可以在 catch 语句块中用 throw 语句抛出这个对象：

```

	Catch(Exception e)
	{
   		...
   		Throw e
	}

```
