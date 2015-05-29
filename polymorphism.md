# C\# 多态性
  
**多态性（polymorphism）** 这个词意味着有多种形式。在面向对象的编程范式中，多态性往往表现为“一个接口，多个函数”。
  

多态性可以是静态的，也可以是动态的。在 **静态多态（static polymorphism）性** 中，一个函数的响应是在编译时确定。**动态多态性（ dynamic polymorphism）** 中，其函数响应是在运行时决定。
  
## 静态多态性
  
在编译时将一个函数与一个对象连接起来的机制被称为早期绑定机制。它也被称为静态绑定。C # 提供了两种技术实现静态多态性。他们是：
  
- 函数重载
  
- 运算符重载
  
我们将在下一章讨论运算符重载。
  
## 函数重载
  
你可以在同一范围对同一函数名有多重定义。该函数的定义必须用不同的类型或参数列表中的参数的数量进行区分。不可以只用不同的返回类型区分不同的重载函数声明。
  
下面的示例显示使用函数 **print()** 打印不同的数据类型：
  
<pre><code>using System;
namespace PolymorphismApplication
{
   class Printdata
   {
      void print(int i)
      {
         Console.WriteLine("Printing int: {0}", i );
      }

      void print(double f)
      {
         Console.WriteLine("Printing float: {0}" , f);
      }

      void print(string s)
      {
         Console.WriteLine("Printing string: {0}", s);
      }
      static void Main(string[] args)
      {
         Printdata p = new Printdata();
         
         // 调用 print 函数打印整型
         p.print(5);
         
         // 调用 print 函数打印浮点型
         p.print(500.263);
         
         // 调用 print 函数打印字符型
         p.print("Hello C++");
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Printing int: 5
Printing float: 500.263
Printing string: Hello C++</code></pre>
  
## 动态多态性
  
C# 允许你创建一个抽象类，被用于提供部分类的接口实现。执行完成时，派生类继承它。**抽象类（Abstract classes）** 包含抽象方法，这是由派生类来实现的。派生类具有更具体化，专业化的功能。
  
以下是关于抽象类的规则：
  
- 你不能创建抽象类的实例
  
- 你不能在抽象类的外部声明抽象方法
  
- 当一个类声明为 **密封的（sealed）** ，它不能被继承，抽象类被不能声明为密封的。
  
下面的程序演示了一个抽象类：
<pre><code>using System;
namespace PolymorphismApplication
{
   abstract class Shape
   {
      public abstract int area();
   }
   class Rectangle:  Shape
   {
      private int length;
      private int width;
      public Rectangle( int a=0, int b=0)
      {
         length = a;
         width = b;
      }
      public override int area ()
      { 
         Console.WriteLine("Rectangle class area :");
         return (width * length); 
      }
   }

   class RectangleTester
   {
      static void Main(string[] args)
      {
         Rectangle r = new Rectangle(10, 7);
         double a = r.area();
         Console.WriteLine("Area: {0}",a);
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Rectangle class area :
Area: 70</code></pre>
  
当你在一个类中有定义函数，并且希望它可以在一个被继承的类中实现功能时，你可以使用**虚函数（virtual functions）** 。虚函数可以在不同的被继承的类中实现，并且将在程序运行时调用此类函数。
  
动态多样性是通过**抽象类**和**虚函数**实现的。
  
下列程序证实了上述说法：

<pre><code>using System;
namespace PolymorphismApplication
{
   class Shape 
   {
      protected int width, height;
      public Shape( int a=0, int b=0)
      {
         width = a;
         height = b;
      }
      public virtual int area()
      {
         Console.WriteLine("Parent class area :");
         return 0;
      }
   }
   class Rectangle: Shape
   {
      public Rectangle( int a=0, int b=0): base(a, b)
      {

      }
      public override int area ()
      {
         Console.WriteLine("Rectangle class area :");
         return (width * height); 
      }
   }
   class Triangle: Shape
   {
      public Triangle(int a = 0, int b = 0): base(a, b)
      {
      
      }
      public override int area()
      {
         Console.WriteLine("Triangle class area :");
         return (width * height / 2); 
      }
   }
   class Caller
   {
      public void CallArea(Shape sh)
      {
         int a;
         a = sh.area();
         Console.WriteLine("Area: {0}", a);
      }
   }  
   class Tester
   {
      
      static void Main(string[] args)
      {
         Caller c = new Caller();
         Rectangle r = new Rectangle(10, 7);
         Triangle t = new Triangle(10, 5);
         c.CallArea(r);
         c.CallArea(t);
         Console.ReadKey();
      }
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Rectangle class area:
Area: 70
Triangle class area:
Area: 25</code></pre>

