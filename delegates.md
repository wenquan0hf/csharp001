# 委托

C# 中的委托类似于 C 或 C++ 中指向函数的指针。**委托**表示引用某个方法的引用类型变量，运行时可以更改引用对象。

特别地，委托可以用于处理事件或回调函数。并且，所有的委托类都是从 **System.Delegate** 类继承而来。

## 声明委托

声明委托时，需要定义能够被委托所引用的方法，任意委托可以引用与该委托拥有相同签名的方法。如：

```
public delegate int MyDelegate (string s);
```

上述委托可以用于引用任何一个以字符型为参数的方法，且返回值类型为整型。

声明委托的句法规则为：

```
delegate <return type> <delegate-name> <parameter list>
```

## 实例化委托

声明委托之后，必须使用 **new** 关键字和一个特定的方法来创建一个委托对象。创建时，传递到 **new** 语句的参数写法与方法调用相同，但是不带有参数，例如：

```
public delegate void printString(string s);
...
printString ps1 = new printString(WriteToScreen);
printString ps2 = new printString(WriteToFile);
```

下述示例演示了委托的声明、实例化，此处的委托用于引用一个带有一个整型参数的方法，且该方法返回一个整型值。

```
using System;

delegate int NumberChanger(int n);
namespace DelegateAppl
{
   class TestDelegate
   {
      static int num = 10;
      public static int AddNum(int p)
      {
         num += p;
         return num;
      }

      public static int MultNum(int q)
      {
         num *= q;
         return num;
      }
      public static int getNum()
      {
         return num;
      }

      static void Main(string[] args)
      {
         // 创建委托实例
         NumberChanger nc1 = new NumberChanger(AddNum);
         NumberChanger nc2 = new NumberChanger(MultNum);
         
         // 使用委托对象调用方法
         nc1(25);
         Console.WriteLine("Value of Num: {0}", getNum());
         nc2(5);
         Console.WriteLine("Value of Num: {0}", getNum());
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Value of Num: 35
Value of Num: 175
```

## 委托的多播

委托对象可通过 "+" 运算符进行合并。一个合并委托可以调用它所合并的两个委托，但只有相同类型的委托可被合并。"-" 运算符则可用于从合并的委托中移除其中一个委托。

利用委托的这种特性，可以创建一个委托被调用时所涉及的方法的调用列表。这被称为委托的**多播**，也叫组播。下面的程序演示了委托的多播：

```
using System;

delegate int NumberChanger(int n);
namespace DelegateAppl
{
   class TestDelegate
   {
      static int num = 10;
      public static int AddNum(int p)
      {
         num += p;
         return num;
      }

      public static int MultNum(int q)
      {
         num *= q;
         return num;
      }
      
      public static int getNum()
      {
         return num;
      }

      static void Main(string[] args)
      {
         // 创建委托实例
         NumberChanger nc;
         NumberChanger nc1 = new NumberChanger(AddNum);
         NumberChanger nc2 = new NumberChanger(MultNum);
         nc = nc1;
         nc += nc2;
         
         // 调用多播
         nc(5);
         Console.WriteLine("Value of Num: {0}", getNum());
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Value of Num: 75
```

## 委托的使用

下面的示例演示了委托的作用，示例中的 *printString* 委托可用于引用带有一个字符串作为输入的方法，且不返回数据。

我们使用这个委托来调用两个方法，第一个方法将字符串输出到控制台，第二个方法将字符串输出到文件：

```
using System;
using System.IO;

namespace DelegateAppl
{
   class PrintString
   {
      static FileStream fs;
      static StreamWriter sw;
      
      // 委托声明
      public delegate void printString(string s);

      // 该方法打印到控制台
      public static void WriteToScreen(string str)
      {
         Console.WriteLine("The String is: {0}", str);
      }
      
      // 该方法打印到文件
      public static void WriteToFile(string s)
      {
         fs = new FileStream("c:\\message.txt",
         FileMode.Append, FileAccess.Write);
         sw = new StreamWriter(fs);
         sw.WriteLine(s);
         sw.Flush();
         sw.Close();
         fs.Close();
      }
      
      // 该方法把委托作为参数，并使用它调用方法
      // call the methods as required
      public static void sendString(printString ps)
      {
         ps("Hello World");
      }
      static void Main(string[] args)
      {
         printString ps1 = new printString(WriteToScreen);
         printString ps2 = new printString(WriteToFile);
         sendString(ps1);
         sendString(ps2);
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
The String is: Hello World
```
