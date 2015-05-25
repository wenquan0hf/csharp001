# 可空类型 - Nullables
C＃提供了一个特殊的数据类型，可空类型，可以在其中指定正常范围值，以及空(null)值。  
例如，在一个可空<Int32>变量中，你可以从-2,147,483,648到2,147,483,647或空值中存储任意值。  
同样，你可以指定true，false或null的Nullable< bool >变量。声明一个可空(Nullable)类型的语法如下：
```
< data_type> ? <variable_name> = null;
```
下面的例子演示了使用可空数据类型：
```
using System;
namespace CalculatorApplication
{
   class NullablesAtShow
   {
      static void Main(string[] args)
      {
         int? num1 = null;
         int? num2 = 45;
         double? num3 = new double?();
         double? num4 = 3.14157;
         
         bool? boolval = new bool?();

         // display the values
         
         Console.WriteLine("Nullables at Show: {0}, {1}, {2}, {3}", num1, num2, num3, num4);
         Console.WriteLine("A Nullable boolean value: {0}", boolval);
         Console.ReadLine();
      }
   }
}
```
编译运行上述代码，得到以下结果：
```
Nullables at Show: , 45,  , 3.14157
A Nullable boolean value:
```
## 空合并运算符(??)
空合并运算符是用于空值类型和引用类型。它是用于一个操作数转换为另一种可为空的(或不为空)值类型的操作数，其中，隐式转换是可能的类型。  
如果第一个操作数的值为null，则该运算符返回第二个操作数的值，否则返回第一个操作数的值。下面的例子说明了这一点：
```
using System;
namespace CalculatorApplication
{
   class NullablesAtShow
   {
      static void Main(string[] args)
      {
         double? num1 = null;
         double? num2 = 3.14157;
         double num3;
         num3 = num1 ?? 5.34;      
         Console.WriteLine(" Value of num3: {0}", num3);
         num3 = num2 ?? 5.34;
         Console.WriteLine(" Value of num3: {0}", num3);
         Console.ReadLine();
      }
   }
}
```
编译运行上述代码，得到以下结果：
```
Value of num3: 5.34
Value of num3: 3.14157
```

