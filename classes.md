# C\# -类
  
当你定义一个类，你实际上定义的是一个数据类型的蓝图。实际上你并没有定义任何数据，但是它定义了类的名字意味着什么。也就是说，一个类的对象由一些可以在该类上进行的操作构成。对象是类的实例。构成类的方法和变量被称为类的成员。
  
## 定义一个类
  
一个类定义以关键字 class 开始，其后跟的是类的名称；类的主体部分体由一对花括号括起来。以下是一个类定义的一般形式：
<pre><code><access specifier> class  class_name
{
   // 成员变量
   <access specifier> <data type> variable1;
   <access specifier> <data type> variable2;
   ...
   <access specifier> <data type> variableN;
   // 成员变量
   <access specifier> <return type> method1(parameter_list)
   {
      // 方法主体
   }
   <access specifier> <return type> method2(parameter_list)
   {
      // 方法主体
   }
   ...
   <access specifier> <return type> methodN(parameter_list)
   {
      // 方法主体
   }
}</code></pre>
  
笔记：
  
- 访问说明符的访问成员的规则与类本身的访问规则相同。如果没有说明，则默认访问的类的类型为 **internal** 。对成员的默认访问类型是 **private** 。
  
- 数据类型指定了变量的类型，如果有返回值的话，返回指定方法的数据类型。
  
- 访问类的成员，可以使用 "." 点运算符。
  
- 点运算符连接的成员的名字和对象的名称。
  
下面的例子说明了到目前为止对于概念的讨论：
<pre><code>using System;
namespace BoxApplication
{
    class Box
    {
       public double length;  // box 的长度
       public double breadth; // box 的宽度
       public double height;  // box 的高度
    }
    class Boxtester
    {
        static void Main(string[] args)
        {
            Box Box1 = new Box();   // 声明 box1 为 box 类型
            Box Box2 = new Box();   // 声明 box2 为 box 类型
            double volume = 0.0;    // 在这里存放 box 的体积

            // box 1 详细数据
            Box1.height = 5.0;
            Box1.length = 6.0;
            Box1.breadth = 7.0;

            // box 2 详细数据
            Box2.height = 10.0;
            Box2.length = 12.0;
            Box2.breadth = 13.0;
           
            // box 1 的体积
            volume = Box1.height * Box1.length * Box1.breadth;
            Console.WriteLine("Volume of Box1 : {0}",  volume);

            // box 2 的体积
            volume = Box2.height * Box2.length * Box2.breadth;
            Console.WriteLine("Volume of Box2 : {0}", volume);
            Console.ReadKey();
        }
    }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Volume of Box1 : 210
Volume of Box2 : 1560</code></pre> 
  
## 成员函数和封装
  
一个类的成员函数有其自己定义或其原型在类的定义中类似于其他变量。它可以操作该类的任何成员对象，并且可以访问一个类的所有成员。
  
成员变量是一个对象的属性（从设计的角度来看），他们都是私有（private）的以便实施封装。这些变量只能被 public 成员函数访问。
  
让我们把上述那些概念来 set 和 get 一个类中不同的类成员的值：
<pre><code>using System;
namespace BoxApplication
{
   class Box
   {
      private double length;   // box 的长度
      private double breadth;  // box 的宽度
      private double height;   // box 的高度
      public void setLength( double len )
      {
         length = len;
      }
      
      public void setBreadth( double bre )
      {
         breadth = bre;
      }
      
      public void setHeight( double hei )
      {
         height = hei;
      }
      public double getVolume()
      {
         return length * breadth * height;
      }
   }
   class Boxtester
   {
      static void Main(string[] args)
      {
         Box Box1 = new Box();   // 将 Box1 声明为 Box 类型
         Box Box2 = new Box();
         double volume;
         
         // 将 Box2 声明为 Box 类型
         // box 1 详细数据
         Box1.setLength(6.0);
         Box1.setBreadth(7.0);
         Box1.setHeight(5.0);
         
         // box 2 详细数据
         Box2.setLength(12.0);
         Box2.setBreadth(13.0);
         Box2.setHeight(10.0);
         
         // box 1 的体积
         volume = Box1.getVolume();
         Console.WriteLine("Volume of Box1 : {0}" ,volume);
         
         // box 2 的体积
         volume = Box2.getVolume();
         Console.WriteLine("Volume of Box2 : {0}", volume);
         
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
  
<pre><code>Volume of Box1 : 210
Volume of Box2 : 1560</code></pre>
  
## C\# 构造函数
  一个类的**构造函数（constructor）**是类的一种特殊的成员函数，当我们创建一个类的新的对象时执行该函数。
  
构造函数与类具有相同的名称，但它没有任何返回类型。下面的例子说明了构造函数的概念：
<pre><code>using System;
namespace LineApplication
{
   class Line
   {
      private double length;   // 线段长度
      public Line()
      {
         Console.WriteLine("Object is being created");
      }

      public void setLength( double len )
      {
         length = len;
      }
      
      public double getLength()
      {
         return length;
      }

      static void Main(string[] args)
      {
         Line line = new Line();    
         
         // 设置线段长度
         line.setLength(6.0);
         Console.WriteLine("Length of line : {0}", line.getLength());
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Object is being created
Length of line : 6</code></pre>
  
**默认构造函数（default constructor）**没有任何的参数，但是如果你需要，构造函数是可以有参数的。这种构造函数被称为**参数化的构造函数（parameterized constructors）**。这种技术有助于你在一个对象被创建时指定它的初始值，如下述示例：
<pre><code>using System;
namespace LineApplication
{
   class Line
   {
      private double length;   // 线段长度
      public Line(double len)  //参数化构造函数
      {
         Console.WriteLine("Object is being created, length = {0}", len);
         length = len;
      }

      public void setLength( double len )
      {
         length = len;
      }
      public double getLength()
      {
         return length;
      }

      static void Main(string[] args)
      {
         Line line = new Line(10.0);
         Console.WriteLine("Length of line : {0}", line.getLength()); 
         
         // 设置线段长度
         line.setLength(6.0);
         Console.WriteLine("Length of line : {0}", line.getLength()); 
         Console.ReadKey();
      }
   }
}</code></pre>
  

编译执行上述代码，得到如下结果：
<pre><code>Object is being created
Length of line : 6
Object is being deleted</code></pre>
  
## C\# 析构函数
**析构函数（destructor）**是类的一种特殊的成员函数，当类的对象在超出作用域时被执行的一种成员函数。一个**析构函数**的名称是在其类名称前加上一个前缀字符（~），它既不能返回一个值，也不能带有任何参数。
  
析构函数对退出程序前释放内存资源时非常有用。析构函数不可以被继承或重载。 
  
下面的示例解释了析构函数的概念：
  
<pre><code>using System;
namespace LineApplication
{
   class Line
   {
      private double length;   // 线段长度
      public Line()  // 构造函数
      {
         Console.WriteLine("Object is being created");
      }
      ~Line() //析构函数
      {
         Console.WriteLine("Object is being deleted");
      }

      public void setLength( double len )
      {
         length = len;
      }
      
      public double getLength()
      {
         return length;
      }

      static void Main(string[] args)
      {
         Line line = new Line();
         
         // 设置线段长度
         line.setLength(6.0);
         Console.WriteLine("Length of line : {0}", line.getLength());           
      }
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Object is being created
Length of line : 6
Object is being deleted</code></pre>


## C\# 类的静态成员
 
我们可以使用 **static** 关键字将类成员定义为静态的。当我们声明一个类的静态成员时，意味着无论有多少类的对象被创建，只有一个副本的静态成员。
  
关键字 **static** 意味着一个类的成员只有一个实例存在。静态变量被用于定义常数，因为他们的值可以通过调用不创建实例的类而被检索出来。静态变量可以在成员函数或者类的定义以外的地方初始化。你也可以在类的定义中初始化静态变量。
  
下面的示例论证了 **静态变量(static variables)** 的使用：
<pre><code>using System;
namespace StaticVarApplication
{
   class StaticVar
   {
      public static int num;
      public void count()
      {
         num++;
      }
      public int getNum()
      {
         return num;
      }
   }
   class StaticTester
   {
      static void Main(string[] args)
      {
         StaticVar s1 = new StaticVar();
         StaticVar s2 = new StaticVar();
         s1.count();
         s1.count();
         s1.count();
         s2.count();
         s2.count();
         s2.count();
         Console.WriteLine("Variable num for s1: {0}", s1.getNum());
         Console.WriteLine("Variable num for s2: {0}", s2.getNum());
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Variable num for s1: 6
Variable num for s2: 6</code></pre>
  
你也可以声明 **static** 的**成员函数**。此类函数只能访问静态变量。静态函数的存在甚至先于创建对象。下面的示例论证了**静态函数（static functions）**的用法：
<pre><code>using System;
namespace StaticVarApplication
{
   class StaticVar
   {
      public static int num;
      public void count()
      {
         num++;
      }
      public static int getNum()
      {
         return num;
      }
   }
   class StaticTester
   {
      static void Main(string[] args)
      {
         StaticVar s = new StaticVar();
         s.count();
         s.count();
         s.count();
         Console.WriteLine("Variable num: {0}", StaticVar.getNum());
         Console.ReadKey();
      }
   }
}</code></pre>
  
编译执行上述代码，得到如下结果：
<pre><code>Variable num: 3
</code></pre>
