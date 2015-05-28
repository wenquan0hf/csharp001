# C\# 运算符重载
  
你可以重新定义或重载大部分 C# 可用的内置操作符。因此，程序员也可以使用用户定义类型的操作符。重载操作符是特殊关键字 **operator** 其后跟被定义的名字的符号。像其他函数一样，重载操作符也有返回类型和参数列表。
  
例如，浏览如下函数：
<pre><code>
public static Box operator+ (Box b, Box c)
{
   Box box = new Box();
   box.length = b.length + c.length;
   box.breadth = b.breadth + c.breadth;
   box.height = b.height + c.height;
   return box;
}</code></pre>
  
上述函数实现了用户定义的 Box 类中加运算符，它增加了两个 Box 对象，并返回这个结果 Box 对象。
  
## 实现运算符重载
  
下列程序显示了完整地实现：
<pre><code>using System;
namespace OperatorOvlApplication
{
   class Box
   {
      private double length;   // box 的长度
      private double breadth;  // box 的宽度
      private double height;   // box 的高度

      public double getVolume()
      {
         return length * breadth * height;
      }
      
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
      
      // 重载 + operator 来增加两个 Box 对象
      public static Box operator+ (Box b, Box c)
      {
         Box box = new Box();
         box.length = b.length + c.length;
         box.breadth = b.breadth + c.breadth;
         box.height = b.height + c.height;
         return box;
      }

   }

   class Tester
   {
      static void Main(string[] args)
      {
         Box Box1 = new Box();    // 声明 box1 为 box 类型
         Box Box2 = new Box();    // 声明 box2 为 box 类型
         Box Box3 = new Box();   // 声明 box3 为 box 类型
         double volume = 0.0;    // 在这里存放 box 的体积

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
         Console.WriteLine("Volume of Box1 : {0}", volume);

         //  box 2 的体积
         volume = Box2.getVolume();
         Console.WriteLine("Volume of Box2 : {0}", volume);

         // 将两个对象相加如下：
         Box3 = Box1 + Box2;

         // box 3 的体积
         volume = Box3.getVolume();
         Console.WriteLine("Volume of Box3 : {0}", volume);
         Console.ReadKey();
      }
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Volume of Box1 : 210
Volume of Box2 : 1560
Volume of Box3 : 5400</code></pre>
  

## 可重载与不可重载的运算符
  
下表列出了 C# 中运算符的可重载能力：
  

| 操作符        | 描述          | 
|：------------- |：-------------|
| +, -, !, ~, ++, --      | 这些一元运算符使用一个操作数，可以被重载。 |
| +, -, *, /, %     | 这些二元运算符使用一个操作数，可以被重载      |
| ==, !=, <, >, <=, >= | 这些比较运算符，可以被重载   |
| &&, \| \|  | 这些条件逻辑运算符不可被直接重载     |
| +=, -=, *=, /=, %= | 赋值运算符不能重载。      |
| =, ., ?:, ->, new, is, sizeof, typeof | 这些运算符不能被重载      |
  
## 示例
针对上述讨论，让我们扩展上面的例子，重载更多的操作符：
<pre><code>using System;
namespace OperatorOvlApplication
{
   class Box
   {
      private double length;   // box 的长度
      private double breadth;  // box 的宽度
      private double height;   // box 的高度
      
      public double getVolume()
      {
         return length * breadth * height;
      }
      
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
      
      // 重载 + operator 来增加两个 Box 对象
      public static Box operator+ (Box b, Box c)
      {
         Box box = new Box();
         box.length = b.length + c.length;
         box.breadth = b.breadth + c.breadth;
         box.height = b.height + c.height;
         return box;
      }
      
      public static bool operator == (Box lhs, Box rhs)
      {
         bool status = false;
         if (lhs.length == rhs.length && lhs.height == rhs.height && lhs.breadth == rhs.breadth)
         {
            status = true;
         }
         return status;
      }
      
      public static bool operator !=(Box lhs, Box rhs)
      {
         bool status = false;
         if (lhs.length != rhs.length || lhs.height != rhs.height || lhs.breadth != rhs.breadth)
         {
            status = true;
         }
         return status;
      }
      
      public static bool operator <(Box lhs, Box rhs)
      {
         bool status = false;
         if (lhs.length < rhs.length && lhs.height < rhs.height && lhs.breadth < rhs.breadth)
         {
            status = true;
         }
         return status;
      }
      
      public static bool operator >(Box lhs, Box rhs)
      {
         bool status = false;
         if (lhs.length > rhs.length && lhs.height > rhs.height && lhs.breadth > rhs.breadth)
         {
            status = true;
         }
         return status;
      }
      
      public static bool operator <=(Box lhs, Box rhs)
      {
         bool status = false;
         if (lhs.length <= rhs.length && lhs.height <= rhs.height && lhs.breadth <= rhs.breadth)
         {
            status = true;
         }
         return status;
      }
      
      public static bool operator >=(Box lhs, Box rhs)
      {
         bool status = false;
         if (lhs.length >= rhs.length && lhs.height >= rhs.height && lhs.breadth >= rhs.breadth)
         {
            status = true;
         }
         return status;
      }
      public override string ToString()
      {
         return String.Format("({0}, {1}, {2})", length, breadth, height);
      }
   }
   
   class Tester
   {
      static void Main(string[] args)
      {
         Box Box1 = new Box();    // 声明 box1 为 box 类型
         Box Box2 = new Box();    // 声明 box2 为 box 类型
         Box Box3 = new Box();    // 声明 box3 为 box 类型
         Box Box4 = new Box();    // 声明 box4 为 box 类型
         double volume = 0.0;    // 这里存放 box 的体积
         
         // box 1 详细数据
         Box1.setLength(6.0);
         Box1.setBreadth(7.0);
         Box1.setHeight(5.0);
         
         // box 2 详细数据
         Box2.setLength(12.0);
         Box2.setBreadth(13.0);
         Box2.setHeight(10.0);
         
         //使用重载的 ToString() 显示 Boxes 
         Console.WriteLine("Box 1: {0}", Box1.ToString());
         Console.WriteLine("Box 2: {0}", Box2.ToString());
         
         // box 1 的体积
         volume = Box1.getVolume();
         Console.WriteLine("Volume of Box1 : {0}", volume);
         
         // box 2 的体积
         volume = Box2.getVolume();
         Console.WriteLine("Volume of Box2 : {0}", volume);
         
         // 将两个对象相加如下：
         Box3 = Box1 + Box2;
         Console.WriteLine("Box 3: {0}", Box3.ToString());
         
         // box 3 的体积
         volume = Box3.getVolume();
         Console.WriteLine("Volume of Box3 : {0}", volume);
         
         //比较 boxes
         if (Box1 > Box2)
            Console.WriteLine("Box1 is greater than Box2");
         else
            Console.WriteLine("Box1 is  greater than Box2");
         
         if (Box1 < Box2)
            Console.WriteLine("Box1 is less than Box2");
         else
            Console.WriteLine("Box1 is not less than Box2");
         
         if (Box1 >= Box2)
            Console.WriteLine("Box1 is greater or equal to Box2");
         else
            Console.WriteLine("Box1 is not greater or equal to Box2");
         
         if (Box1 <= Box2)
            Console.WriteLine("Box1 is less or equal to Box2");
         else
            Console.WriteLine("Box1 is not less or equal to Box2");
         
         if (Box1 != Box2)
            Console.WriteLine("Box1 is not equal to Box2");
         else
            Console.WriteLine("Box1 is not greater or equal to Box2");
         Box4 = Box3;
         
         if (Box3 == Box4)
            Console.WriteLine("Box3 is equal to Box4");
         else
            Console.WriteLine("Box3 is not equal to Box4");
         
         Console.ReadKey();
      }
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Box 1: (6, 7, 5)
Box 2: (12, 13, 10)
Volume of Box1 : 210
Volume of Box2 : 1560
Box 3: (18, 20, 15)
Volume of Box3 : 5400
Box1 is not greater than Box2
Box1 is less than Box2
Box1 is not greater or equal to Box2
Box1 is less or equal to Box2
Box1 is not equal to Box2
Box3 is equal to Box4</code></pre>


