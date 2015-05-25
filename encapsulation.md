# C#-封装

**封装**的定为义“作为在一个物理或逻辑封装包封一个或多个项目的过程”。封装，面向对象的编程方法，阻止访问的实现细节。

抽象和封装是面向对象编程相关的特性。抽象允许制作相关的信息可见和封装使程序员来实现抽象所需的水平。

封装是通过使用**访问修辞符**来实现。**访问修辞符**定义一个类成员的范围和可视度。C# 支持以下访问修辞符：

- Public

- Private

- Protected

- Internal

- Protected internal

##  Public 访问修辞符

公共访问说明允许一个类的成员变量和成员函数暴露在其他功能和对象。任何公共成员可以从类的外部访问。

下面的例子说明了这一点：
```
using System;
namespace RectangleApplication
{
   class Rectangle
   {
      //member variables
      public double length;
      public double width;
      
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
   }//end class Rectangle
   
   class ExecuteRectangle
   {
      static void Main(string[] args)
      {
         Rectangle r = new Rectangle();
         r.length = 4.5;
         r.width = 3.5;
         r.Display();
         Console.ReadLine();
      }
   }
}
```

我们编译和运行上面的程序，将产生以下结果：
```
Length: 4.5
Width: 3.5
Area: 15.75
```

在上面的例子中，成员变量的 length 和 width 都声明为 public，这样它们就可以使用 Rectangle 类，命名实例 r 通过函数 main() 进行访问。

成员函数 Display() 和 getArea() 也可以直接访问这些变量不使用类的任何实例。

成员函数 Display() 也被声明为 public，所以从 Main() 使用 Rectangle 类，命名为 r 的一个实例也可以被访问。

## Private 访问修辞符

私有访问符允许类从其他职能和对象隐藏其成员变量和成员函数。只有同一个类的函数可以访问它的私有成员。即使是一个类的实例也不能访问它的私有成员。

下面的例子说明了这一点：
```
using System;
namespace RectangleApplication 
{
   class Rectangle
   {
      //member variables
      private double length;
      private double width;
      
      public void Acceptdetails()
      {
         Console.WriteLine("Enter Length: ");
         length = Convert.ToDouble(Console.ReadLine());
         Console.WriteLine("Enter Width: ");
         width = Convert.ToDouble(Console.ReadLine());
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
   }//end class Rectangle
   
   class ExecuteRectangle
   {
      static void Main(string[] args)
      {
         Rectangle r = new Rectangle();
         r.Acceptdetails();
         r.Display();
         Console.ReadLine();
      }
   }
}
```

我们编译和运行上面的程序，将产生以下结果：
```
Enter Length:
4.4
Enter Width:
3.3
Length: 4.4
Width: 3.3
Area: 14.52
```

在上面的例子中，成员变量的 length 和 width 都声明为 private，所以它们不能从 main() 函数访问。成员函数 AcceptDetails() 和 Display() 可以访问这些变量。由于成员函数 AcceptDetails() 和 Display() 被声明为 public，它们可以从 Main() 函数中使用 Rectangle 类，命名为 r 的一个实例访问。


## Protected 访问修辞符

Protected 访问修辞符允许子类来访问其基类的成员变量和成员函数。这种方式有助于实现继承。我们将在继承这一章节详细讨论这个问题。

## Internal 访问修辞符

内部访问符允许类的成员变量和成员函数暴露在其他功能和对象在当前汇编。换句话说，使用内部访问说明任何成员都可以从在其中构件被定义在应用程序中定义的任何类或方法来访问。

下面的程序说明了这一点：
```
using System;
namespace RectangleApplication
{
   class Rectangle
   {
      //member variables
      internal double length;
      internal double width;
      
      double GetArea()
      {
         return length * width;
      }
      public void Display()
      {
         Console.WriteLine("Length: {0}", length);
         Console.WriteLine("Width: {0}", width);
         Console.WriteLine("Area: {0}", GetArea());
      }
   }//end class Rectangle
   
   class ExecuteRectangle
   {
      static void Main(string[] args)
      {
         Rectangle r = new Rectangle();
         r.length = 4.5;
         r.width = 3.5;
         r.Display();
         Console.ReadLine();
      }
   }
}
```

我们编译和运行上面的程序，将产生以下结果：
```
Length: 4.5
Width: 3.5
Area: 15.75
```

在上面的例子中，注意到成员函数 getArea() 无任何访问说明符声明。那么这将是一个类成员的默认访问说明，如果我们任何都不声明？这是私有的。

## Protected internal 访问修辞符

受保护的内部访问符允许一个类从其他类对象和函数隐藏其成员变量和成员函数，除了相同的应用程序中的子类。这在实现继承中也有使用。








