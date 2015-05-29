# C\# 循环

可能在有的情况下，需要多次执行代码块。一般是语句顺序执行：在一个函数的第一条语句，首先执行，然后是第二个等等。

编程语言提供了各种控制结构，允许更多复杂的执行路径。

循环语句可以让我们多次执行一个语句或一组语句，下面是在大多数编程语言循环的一般语句：

![image](images/loop_architecture.jpg)

C# 提供了以下类型的循环来处理循环需求。点击以下链接查看其详细信息。

|循环类型 | 描述 |
| ----- | ----- |
| **[while 循环](http://www.tutorialspoint.com/csharp/csharp_while_loop.htm)**|重复声明语句或一组，而给定的条件为真，它测试条件为执行循环体前|
| **[for 循环](http://www.tutorialspoint.com/csharp/csharp_for_loop.htm)**|多次执行一个语句序列，简化代码，管理循环变量|
| **[do...while 循环](http://www.tutorialspoint.com/csharp/csharp_do_while_loop.htm)**|像一个 while 语句，不同之处在于它测试条件在循环体的结尾|
|**[嵌套循环](http://www.tutorialspoint.com/csharp/csharp_nested_loops.htm)**|可以使用一个或多个循环的同时支持 do..while 循环|

## 循环控制语句

循环控制语句改变其正常的顺序执行。当执行离开一个范围，在该范围内创建的所有对象自动被销毁。

C# 提供了以下控制语句。点击以下链接查看他们的详细资料。

| 控制语句 | 描述 |
| ----- | ----- |
| **[break 语句](http://www.tutorialspoint.com/csharp/csharp_break_statement.htm)**|终止循环或 switch 语句并将执行立即循环或 switch 下面的语句|
| **[continue 语句](http://www.tutorialspoint.com/csharp/csharp_continue_statement.htm)**|导致循环跳过它主体的其余部分，并在其条件重申之前立即重新测试|

## 无限循环

如果条件永远不会为假，一个循环则变为无限循环。 for 循环传统上用于此目的。由于形成 for 循环都需要三个表达式，则可以将条件表达式空，则做成一个死循环。

**举例**
```
using System;
namespace Loops
{
   class Program
   {
      static void Main(string[] args)
      {
         for (; ; )
         {
            Console.WriteLine("Hey! I am Trapped");
         }
      }
   }
} 
```

当条件表达式不存在时，它被假定为真 (true)。可能有一个初始化和增量的表达，但程序员更普遍使用 for(;;) 结构来表示一个无限循环。
