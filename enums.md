# C\# 枚举
枚举是一组命名的整型常量。枚举类型使用 enum 关键字声明。  
C# 枚举是值的数据类型。换句话说，枚举包含它自己的值，不能继承或被继承。
## 声明枚举变量
用于声明枚举的一般语法：
```
enum <enum_name> 
{ 
    enumeration list 
};
```
这里
-	enum_name 指定枚举类型名称。
-	enumeration list 是一个逗号分隔的标识符的列表。  

每个枚举列表中的符号表示整数值，比它前面的符号一个更大。  
缺省情况下，第一枚举符号的值是 0。  
  
例如：
```
enum Days { Sun, Mon, tue, Wed, thu, Fri, Sat };
```
## 示例
下面的例子演示了使用枚举变量：
```
using System;
namespace EnumApplication
{
   class EnumProgram
   {
      enum Days { Sun, Mon, tue, Wed, thu, Fri, Sat };

      static void Main(string[] args)
      {
         int WeekdayStart = (int)Days.Mon;
         int WeekdayEnd = (int)Days.Fri;
         Console.WriteLine("Monday: {0}", WeekdayStart);
         Console.WriteLine("Friday: {0}", WeekdayEnd);
         Console.ReadKey();
      }
   }
}
```
编译和执行上述代码，得到如下结果：
```
Monday: 1
Friday: 5
```
