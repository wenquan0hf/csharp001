# 方法-Method
方法是一组在一起执行任务的语句。每个 C# 程序都至少有一个含有方法的类，名为 Main。   
若要使用方法，您需要：
- 定义一个方法
- 调用方法  
  

## 在 C\# 中定义方法
当你定义一个方法时，你基本上要声明其结构的组成元素。在 C# 中定义方法的语法如下所示：  
```
<Access Specifier> <Return Type> <Method Name>(Parameter List)
{
   Method Body
}
```
  
以下是方法中的各种元素：  
- 访问说明符- Access Specifier： 它用于从一个类中确定一个变量或方法的可见性。
- 返回类型- Return type： 方法可能会返回一个值。返回类型是方法返回值的数据类型。如果该方法不返回任何值，那么返回类型是 void。
- 方法名称- Method name： 方法名称是唯一的标识符，并区分大小写。它不能与在类中声明的任何其他标识符相同。
- 参数列表- Parameter list： 括号括起来，使用参数从方法中传递和接收数据。参数列表是指类型、 顺序和方法的参数数目。参数是可选的 ；方法可能包含任何参数。
- 方法主体- Method body： 它包含的一组指令完成所需要的活动所需。
  
示例
下面的代码段显示了一个函数 FindMax，从两个整数值中，返回其中较大的一个。它具有公共访问说明符，所以它可以通过使用类的外部例子来访问。
```
class NumberManipulator
{
   public int FindMax(int num1, int num2)
   {
      /* local variable declaration */
      int result;

      if (num1 > num2)
         result = num1;
      else
         result = num2;

      return result;
   }
   ...
}
```
## 在 C\# 中调用方法
你可以使用方法的名称来调用方法。下面的示例说明了这一点：
```
using System;
namespace CalculatorApplication
{
   class NumberManipulator
   {
      public int FindMax(int num1, int num2)
      {
         /* local variable declaration */
         int result;
         
         if (num1 > num2)
            result = num1;
         else
            result = num2;
         return result;
      }
      static void Main(string[] args)
      {
         /* local variable definition */
         int a = 100;
         int b = 200;
         int ret;
         NumberManipulator n = new NumberManipulator();

         //calling the FindMax method
         ret = n.FindMax(a, b);
         Console.WriteLine("Max value is : {0}", ret );
         Console.ReadLine();
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
Max value is : 200
```
你也可以通过使用类的实例来从其他类中调用公开方法。  
例如，FindMax 它属于 NumberManipulator 类中的方法，你可以从另一个类测试中调用它。
```
using System;
namespace CalculatorApplication
{
   class NumberManipulator
   {
      public int FindMax(int num1, int num2)
      {
         /* local variable declaration */
         int result;
         
         if(num1 > num2)
            result = num1;
         else
            result = num2;
         
         return result;
      }
   }
   
   class Test
   {
      static void Main(string[] args)
      {
         /* local variable definition */
         int a = 100;
         int b = 200;
         int ret;
         NumberManipulator n = new NumberManipulator();
         
         //calling the FindMax method
         ret = n.FindMax(a, b);
         Console.WriteLine("Max value is : {0}", ret );
         Console.ReadLine();
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
Max value is : 200
```
## 递归方法调用- Recursive Method Call

有一种方法可以调用本身。这就是所谓的递归。下面是使用递归函数计算一个给定数字阶乘的示例：
```
using System;
namespace CalculatorApplication
{
   class NumberManipulator
   {
      public int factorial(int num)
      {
         /* local variable declaration */
         int result;
         if (num == 1)
         {
            return 1;
         }
         else
         {
            result = factorial(num - 1) * num;
            return result;
         }
      }
      
      static void Main(string[] args)
      {
         NumberManipulator n = new NumberManipulator();
         //calling the factorial method
         Console.WriteLine("Factorial of 6 is : {0}", n.factorial(6));
         Console.WriteLine("Factorial of 7 is : {0}", n.factorial(7));
         Console.WriteLine("Factorial of 8 is : {0}", n.factorial(8));
         Console.ReadLine();
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
Factorial of 6 is: 720
Factorial of 7 is: 5040
Factorial of 8 is: 40320
```
## 将参数传递给方法- Passing Parameters to a Method

当调用带参数的方法时，您需要将参数传递给该方法。  
有三种方法，可以将参数传递给方法：


| 方法   |	 描述  |
| -------- | --------- |
|值参数    |此方法将参数的实际值复制到该函数的形参。在这种情况下，对该参数在函数内部所做的更改没有对参数产生影响。 |
|引用参数	 |此方法将对实参的内存位置的引用复制到形参。这意味着对参数所做的更改会影响参数本身。                     |
|输出参数  |这种方法有助于返回多个值。    |

