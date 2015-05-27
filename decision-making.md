# C#-决策

决策结构需要程序员指定一个或多个条件进行评估，或由程序进行测试，如果条件被确定为真，那么一条或多条语句被执行，如果条件被执行被确定为假，那么任选的其它语句执行。

以下是从在大多数编程语言中找到的典型决策结构形式：

![image](images/decision_making.jpg)

C# 提供了以下几种类型的决策语句。点击以下链接查看其详细信息。

| 语句 | 描述 |
| ------ | ------ |
|[if 语句](http://www.tutorialspoint.com/csharp/if_statement_in_csharp.htm)|if 语句包含一个布尔表达式后跟一个或多个语句|
|[if...else 语句](http://www.tutorialspoint.com/csharp/if_else_statement_in_csharp.htm)|if 语句可以跟着一个可选的 else 语句，布尔表达式是假时，else 语句执行|
|[嵌套 if 语句](http://www.tutorialspoint.com/csharp/nested_if_statements_in_csharp.htm)|可以使用一个 if 或 else if 在另一个 if 或 else if 语句中|
|[switch 语句](http://www.tutorialspoint.com/csharp/switch_statement_in_csharp.htm)| switch 语句可以让一个变量对立值的列表平等进行测试|
|[嵌套 switch 语句](http://www.tutorialspoint.com/csharp/nested_switch_statements_in_csharp.htm)|可以使用一个 switch 语句中的另一个 switch |

## ? : 运算符：

我们已经介绍条件运算符 **? :** 在前面的章节中可以用来代替 **if...else** 语句。它具有以下的一般形式：

```
Exp1 ? Exp2 : Exp3;
```

在这里计算 Exp1，Exp2 和 Exp3 表达式。注意使用和放置。

a? 表达式是确定这样的：Exp1 评估计算。如果结果为 true，那么 Exp2 后进行评估，并成为整个值 ? 表达式。如果计算 Exp1 是假的，那么 Exp3 评估计算，它的值变为表达式的值。
