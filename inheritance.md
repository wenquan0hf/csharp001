# C\# 继承
  
面向对象程序设计中最重要的一个概念就是继承（inheritance）。继承允许我们在另一个类来定义另一个类，这使得它更容易创建和维护一个应用程序。这也提供了一个机会来重用代码的功能，加快实现时间。
  
创建一个类的时候，不是要写全新的数据成员和成员函数，程序员可以指定新的类继承一个已经存在的类的成员。已有的类称为**基类（base class）**，新的类称为**派生类（derived class）**。
  
继承的思想实现了 **IS-A** 的关系。例如，哺乳动物是（IS-A）动物，狗是（IS-A）哺乳动物，因此狗是（IS-A）一个动物等。
  
## 基类和派生类
  
一个类可以从多个类或接口被派生，这意味着它可以从多个基类或接口继承数据和函数。
  
用 C# 创建派生类的语法如下：
<pre><code><acess-specifier> class <base_class>
{
   ...
}
class <derived_class> : <base_class>
{
   ...
}</code></pre>
  
比如基类为 Shape ，其派生类为 Rectangle ：
<pre><code>using System;
namespace InheritanceApplication
{
   class Shape 
   {
      public void setWidth(int w)
      {
         width = w;
      }
      public void setHeight(int h)
      {
         height = h;
      }
      protected int width;
      protected int height;
   }

   // 派生类
   class Rectangle: Shape
   {
      public int getArea()
      { 
         return (width * height); 
      }
   }
   
   class RectangleTester
   {
      static void Main(string[] args)
      {
         Rectangle Rect = new Rectangle();

         Rect.setWidth(5);
         Rect.setHeight(7);

         // 打印对象的面积
         Console.WriteLine("Total area: {0}",  Rect.getArea());
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：

<pre><code>Total area: 35</code></pre>
  
## 初始化基类
  
派生类继承基类的成员变量和成员方法。因此，父类对象应该是先于子类被创建。你可以在初始化列表中说明父类的初始化。
  
下面的程序论证了上述方法：
<pre><code>using System;
namespace RectangleApplication
{
   class Rectangle
   {
      //成员变量
      protected double length;
      protected double width;
      public Rectangle(double l, double w)
      {
         length = l;
         width = w;
      }
      
      public double GetArea()
      {
         return length * width;
      }
      
      public void Display()
      {
         Console.WriteLine("Length: {0}", length);
         Console.WriteLine("Width: {0}", width);
         Console.WriteLine("Area: {0}", GetArea());
      }
   }// Rectangle 类结束  
   
   class Tabletop : Rectangle
   {
      private double cost;
      public Tabletop(double l, double w) : base(l, w)
      { }
      public double GetCost()
      {
         double cost;
         cost = GetArea() * 70;
         return cost;
      }
      public void Display()
      {
         base.Display();
         Console.WriteLine("Cost: {0}", GetCost());
      }
   }
   class ExecuteRectangle
   {
      static void Main(string[] args)
      {
         Tabletop t = new Tabletop(4.5, 7.5);
         t.Display();
         Console.ReadLine();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Length: 4.5
Width: 7.5
Area: 33.75
Cost: 2362.5</code></pre>
  
## C\# 中的多重继承
  
**C# 不支持多重继承**。但是你可以使用接口来实现多重继承。下面的程序实现了该功能：
<pre><code>using System;
namespace InheritanceApplication
{
   class Shape 
   {
      public void setWidth(int w)
      {
         width = w;
      }
      public void setHeight(int h)
      {
         height = h;
      }
      protected int width;
      protected int height;
   }

   // 基类 PaintCost
   public interface PaintCost 
   {
      int getCost(int area);

   }
   
   // 派生类
   class Rectangle : Shape, PaintCost
   {
      public int getArea()
      {
         return (width * height);
      }
      public int getCost(int area)
      {
         return area * 70;
      }
   }
   class RectangleTester
   {
      static void Main(string[] args)
      {
         Rectangle Rect = new Rectangle();
         int area;
         Rect.setWidth(5);
         Rect.setHeight(7);
         area = Rect.getArea();
         
         //打印对象面积
         Console.WriteLine("Total area: {0}",  Rect.getArea());
         Console.WriteLine("Total paint cost: ${0}" , Rect.getCost(area));
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Total area: 35
Total paint cost: $2450</code></pre>
