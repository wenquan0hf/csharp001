## C\# -命名空间
  
**命名空间（namespace）** 专为提供一种来保留一套独立名字与其他命名区分开来的方式。一个命名空间中声明的类的名字与在另一个命名空间中声明的相同的类名并不会发生冲突。
  
## 命名空间的定义
  
命名空间的定义以关键字 **namespace** 开始，其后跟命名空间的名称：
<pre><code>namespace namespace_name
{
   // 代码声明
}</code></pre>
  
调用的函数或变量的命名空间启用版本，在命名空间名称如下：
<pre><code>namespace_name.item_name;
</code></pre>
  
下面的程序演示了命名空间的使用：
<pre><code>using System;
namespace first_space
{
   class namespace_cl
   {
      public void func()
      {
         Console.WriteLine("Inside first_space");
      }
   }
}

namespace second_space
{
   class namespace_cl
   {
      public void func()
      {
         Console.WriteLine("Inside second_space");
      }
   }
}

class TestClass
{
   static void Main(string[] args)
   {
      first_space.namespace_cl fc = new first_space.namespace_cl();
      second_space.namespace_cl sc = new second_space.namespace_cl();
      fc.func();
      sc.func();
      Console.ReadKey();
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Inside first_space
Inside second_space</code></pre>
  
## 关键字 using

关键词 **using** 指出了该程序是在使用给定的命名空间的名称。例如，我们在程序中使用的是系统命名空间。其中有 Console 类的定义。我们只需要写：
<pre><code>Console.WriteLine ("Hello there");
</code></pre>
  
我们还可以写完全限定名称：
<pre><code>System.Console.WriteLine("Hello there");
</code></pre>

你也可以使用**using** 指令避免还要在前面加上 namespace 。这个指令会告诉编译器后面的代码使用的是在指定的命名空间中的名字。命名空间是因此包含下面的代码：
  
让我们重写前面的示例，使用 using 指令：
<pre><code>using System;
using first_space;
using second_space;

namespace first_space
{
   class abc
   {
      public void func()
      {
         Console.WriteLine("Inside first_space");
      }
   }
}

namespace second_space
{
   class efg
   {
      public void func()
      {
         Console.WriteLine("Inside second_space");
      }
   }
}   

class TestClass
{
   static void Main(string[] args)
   {
      abc fc = new abc();
      efg sc = new efg();
      fc.func();
      sc.func();
      Console.ReadKey();
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Inside first_space
Inside second_space</code></pre>
  
## 嵌套命名空间
  
你可以在一个命名空间中定义另一个命名空间，方法如下：
<pre><code>namespace namespace_name1
{
   // 代码声明
   namespace namespace_name2
   {
    //代码声明
   }
}</code></pre>
你可以使用点运算符“.”来访问嵌套命名空间中的成员
<pre><code>using System;
using first_space;
using first_space.second_space;

namespace first_space
{
   class abc
   {
      public void func()
      {
         Console.WriteLine("Inside first_space");
      }
   }
   namespace second_space
   {
      class efg
      {
         public void func()
         {
            Console.WriteLine("Inside second_space");
         }
      }
   }   
}
 
class TestClass
{
   static void Main(string[] args)
   {
      abc fc = new abc();
      efg sc = new efg();
      fc.func();
      sc.func();
      Console.ReadKey();
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Inside first_space
Inside second_space</code></pre>



