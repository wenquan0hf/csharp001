# C# 程序结构

在我们学习 C# 编程语言的基础构件块之前，让我们先看一下 C# 的最小的程序结构，
以便作为接下来章节的参考。

## 创建 Hello World 实例

一个 C# 程序主要包括以下部分：

- 命名空间声明
- 一个类
- 类方法
- 类属性
- 一个 Main 方法
- 语句和表达式
- 注释

让我们看一个可以打印出 "Hello World" 的简单的代码：

```
using System;
namespace HelloWorldApplication
{
   class HelloWorld
   {
      static void Main(string[] args)
      {
         /* 我的第一个 C# 程序*/
         Console.WriteLine("Hello World");
         Console.ReadKey();
      }
   }
}
```
编译执行上述代码，得到如下结果：

```
Hello World
```

让我们看一下上面给出程序的各个部分：

- 程序的第一行 **using System**;-**using** 关键字用于在程序中包含 **System** 命名空间。 一个程序一般有多个 **using** 语句。
- 下一行是 **namespace** 声明。一个 **namespace** 是一系列的类。*HelloWorldApplication* 命名空间包含了类 *HelloWorld* 。
- 下一行是 **class** 声明。类 *HelloWorld* 包含了程序所使用的数据和方法的声明。类一般包含多个方法。方法定义了类的行为。
在这里，*HelloWorld* 类只有一个 **Main** 方法。
- 下一行定义了 **Main** 方法，是所有 C# 程序的**入口**。**Main** 方法说明当类执行时，它将做什么动作。
- 下一行 /\*...\*/ 将会被编译器忽略，且它会在程序中添加**注释** 。
- Main 方法通过语句 **Console.WriteLine("Hello World");** 指定了它的行为。
*WriteLine* 是一个定义在 *System* 命名空间中的 *Console* 类的一个方法。该语句会在屏幕上显示消息 "Hello, World!" 。
- 最后一行 **Console.ReadKey();** 是针对 VS.NET 用户的。这使得程序会等待一个用户按键的动作，防止程序在 Visual Studio .NET 启动时屏幕会快速运行并关闭。

以下几点值得注意：

- C# 是大小写敏感的。
- 所有的语句和表达式必须以分号（;）结尾。
- 程序的执行从 Main 方法开始。
- 与 Java 不同的是，文件名可以不同于类的名称。

# 编译执行 C# 程序

如果您使用 Visual Studio.Net 编译和执行 C# 程序，请按下面的步骤进行：

- 启动 Visual Studio。
- 在菜单栏上，选择 File -> New -> Project。
- 从模板中选择 Visual C#，然后选择 Windows。
- 选择 Console Application。
- 为您的项目制定一个名称，然后点击 OK 按钮。
- 新项目会出现在解决方案资源管理器中。
- 在代码编辑器中编写代码。
- 点击 Run 按钮或者按下 F5 键来运行程序。会出现一个命令提示符窗口，显示 Hello World。

您也可以使用命令行代替 Visual Studio IDE 来编译 C# 程序：

- 打开一个文本编辑器，添加上面提到的代码。
- 保存文件为 **helloworld.cs**。
- 打开命令提示符工具，定位到文件所保存的目录。
- 键入 **csc helloworld.cs** 并按下回车键来编译代码。
- 如果代码没有错误，命令提示符会进入下一行，并生成 **helloworld.exe** 可执行文件。
- 接下来，键入 **helloworld** 来执行程序。
- 您将看到 "Hello World" 打印在屏幕上。
