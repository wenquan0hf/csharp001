# C\# 泛型
**泛型**允许推迟类或方法中编程元素的数据类型规范的编写，直到实际在程序中使用它的时候再编写。换句话说，泛型允许编写一个可以与任何数据类型协作的类或方法。

你可以通过数据类型的替代参数来编写类或方法的规范。当编译器遇到类的构造函数或方法的函数调用时，它会生成代码来处理指定的数据类型。下面这个简单的示例将有助于理解这个概念：

```
using System;
using System.Collections.Generic;

namespace GenericApplication
{
   public class MyGenericArray<T>
   {
      private T[] array;
      public MyGenericArray(int size)
      {
         array = new T[size + 1];
      }
      
      public T getItem(int index)
      {
         return array[index];
      }
      
      public void setItem(int index, T value)
      {
         array[index] = value;
      }
   }
   
   class Tester
   {
      static void Main(string[] args)
      {
         
         // 声明一个整型数组
         MyGenericArray<int> intArray = new MyGenericArray<int>(5);
         
         // 设置值
         for (int c = 0; c < 5; c++)
         {
            intArray.setItem(c, c*5);
         }
         
         // 获取值
         for (int c = 0; c < 5; c++)
         {
            Console.Write(intArray.getItem(c) + " ");
         }
         
         Console.WriteLine();
         
         // 声明一个字符数组
         MyGenericArray<char> charArray = new MyGenericArray<char>(5);
         
         // 设置值
         for (int c = 0; c < 5; c++)
         {
            charArray.setItem(c, (char)(c+97));
         }
         
         // 获取值
         for (int c = 0; c< 5; c++)
         {
            Console.Write(charArray.getItem(c) + " ");
         }
         Console.WriteLine();
         
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
0 5 10 15 20
a b c d e
```

## 泛型的特性
泛型是一种可以增强程序功能的技术，表现在如下几个方面：

*	它有助于最大限度地进行重用代码、确保类型的安全以及提高性能。
*	你可以创建泛型集合类。.NET 框架类库在 *System.Collections.Generic* 命名空间中包含了一些新的泛型集合类，你可以使用这些泛型集合类来替代 *System.Collections* 中的集合类。
*	你可以创建自己的泛型接口、泛型类、泛型方法、泛型事件和泛型委托。
*	你可以对泛型类进行约束，使其只访问具有特定数据类型的方法。
*	在运行时，通过使用反射方法可以获取泛型数据类型中所使用的类型信息。

## 泛型方法

在之前的例子中，我们使用过一个泛型类，我们还可以通过类型参数来声明泛型方法。下述示例很好地展示了这个概念：

```
using System;
using System.Collections.Generic;

namespace GenericMethodAppl
{
   class Program
   {
      static void Swap<T>(ref T lhs, ref T rhs)
      {
         T temp;
         temp = lhs;
         lhs = rhs;
         rhs = temp;
      }
      static void Main(string[] args)
      {
         int a, b;
         char c, d;
         a = 10;
         b = 20;
         c = 'I';
         d = 'V';
         
         // 显示交换之前的值
         Console.WriteLine("Int values before calling swap:");
         Console.WriteLine("a = {0}, b = {1}", a, b);
         Console.WriteLine("Char values before calling swap:");
         Console.WriteLine("c = {0}, d = {1}", c, d);
         
         // 调用 swap 进行交换
         Swap<int>(ref a, ref b);
         Swap<char>(ref c, ref d);
         
         // 显示交换之后的值
         Console.WriteLine("Int values after calling swap:");
         Console.WriteLine("a = {0}, b = {1}", a, b);
         Console.WriteLine("Char values after calling swap:");
         Console.WriteLine("c = {0}, d = {1}", c, d);
         
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Int values before calling swap:
a = 10, b = 20
Char values before calling swap:
c = I, d = V
Int values after calling swap:
a = 20, b = 10
Char values after calling swap:
c = V, d = I
```

## 泛型委托
你可以通过类型参数来定义一个泛型委托，如：

```
delegate T NumberChanger<T>(T n);
```
泛型委托示例：

```
using System;
using System.Collections.Generic;

delegate T NumberChanger<T>(T n);
namespace GenericDelegateAppl
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
         NumberChanger<int> nc1 = new NumberChanger<int>(AddNum);
         NumberChanger<int> nc2 = new NumberChanger<int>(MultNum);
         
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

编译执行以上代码，得到如下结果：

```
Value of Num: 35
Value of Num: 175
```
