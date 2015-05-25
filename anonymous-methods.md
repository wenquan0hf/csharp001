# C\# 匿名方法
先前的章节中提过，委托是用于引用与其具有相同签名的方法，即使用委托对象，就可以调用任何被该委托引用的方法。

**匿名方法**提供了一种将一段代码块作为委托参数的技术。顾名思义，匿名方法没有名字，只有方法主体。

你不需要为匿名方法指定返回类型，其返回类型直接由方法主体推断而来。

## 编写匿名方法
匿名方法通过使用 **delegate** 关键字创建委托实例来实现方法的声明，如：

```
delegate void NumberChanger(int n);
...
NumberChanger nc = delegate(int x)
{
   Console.WriteLine("Anonymous Method: {0}", x);
};
```

上述代码块中的 *Console.WriteLine("Anonymous Method: {0}", x);* 就是匿名方法的主体。

委托可以通过匿名方法调用，也可以通过命名方法调用，即，通过向委托对象来传递方法参数，如：

```
nc(10);
```

示例

```
using System;

delegate void NumberChanger(int n);
namespace DelegateAppl
{
   class TestDelegate
   {
      static int num = 10;
      public static void AddNum(int p)
      {
         num += p;
         Console.WriteLine("Named Method: {0}", num);
      }
      
      public static void MultNum(int q)
      {
         num *= q;
         Console.WriteLine("Named Method: {0}", num);
      }
      
      public static int getNum()
      {
         return num;
      }
      static void Main(string[] args)
      {
         //create delegate instances using anonymous method
         NumberChanger nc = delegate(int x)
         {
            Console.WriteLine("Anonymous Method: {0}", x);
         };
         
         //calling the delegate using the anonymous method 
         nc(10);
         
         //instantiating the delegate using the named methods 
         nc =  new NumberChanger(AddNum);
         
         //calling the delegate using the named methods 
         nc(5);
         
         //instantiating the delegate using another named methods 
         nc =  new NumberChanger(MultNum);
         
         //calling the delegate using the named methods 
         nc(2);
         Console.ReadKey();
      }
   }
}
```
编译执行上述代码，得到如下结果：

```
Anonymous Method: 10
Named Method: 15
Named Method: 30
```
