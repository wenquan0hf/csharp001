# C# - 属性

属性是类、结构和接口的命名成员。类或结构中的成员变量或方法称为域。属性是域的扩展，且可使用相同的语法来访问。它们使用访问器让私有域的值可被读写或操作。

属性不会确定存储位置。相反，它们具有可读写或计算它们值的访问器。

例如，有一个名为 Student 的类，带有 age、name 和 code 的私有域。我们不能在类的范围以外直接访问这些域，但是我们可以拥有访问这些私有域的属性。

## 访问器
属性的访问器包含有助于获取（读取或计算）或设置（写入）属性的可执行语句。访问器声明可包含一个 get 访问器、一个 set 访问器，或者同时包含二者。例如：

```

    // 为字符类型声明一个叫Code的属性：
	public string Code
	{
   		get
   		{
      		return code;
   		}
   		set
   		{
      		code = value;
   		}
	}

	// 为字符类型声明一个叫Name的属性：
	public string Name
	{
   		get
   		{
      		return name;
   		}
   		set
   		{
      		name = value;
   		}
	}

	// 为整形类型声明一个叫Age的属性：
	public int Age
	{ 
   		get
   		{
      		return age;
   		}
   		set
   		{
      		age = value;
   		}
	}
```

## 示例

下面的程序说明了特性是如何使用的：


```

    using System;
	namespace tutorialspoint
	{
   	class Student
   	{
      private string code = "N.A";
      private string name = "not known";
      private int age = 0;
      
      // 为字符类型声明一个叫Code的属性：
      public string Code
      {
         get
         {
            return code;
         }
         set
         {
            code = value;
         }
      }
      
      // 为字符类型声明一个叫Name的属性：
      public string Name
      {
         get
         {
            return name;
         }
         set
         {
            name = value;
         }
      }
      
      // 为整形类型声明一个叫Age的属性：
      public int Age
      {
         get
         {
            return age;
         }
         set
         {
            age = value;
         }
      }
      public override string ToString()
      {
         return "Code = " + Code +", Name = " + Name + ", Age = " + Age;
      }
   	}
   
   	class ExampleDemo
   	{
      public static void Main()
      {
      
         // 创建一个Student类的对象
         Student s = new Student();
         
         // 为student对象设置code，name和age
         s.Code = "001";
         s.Name = "Zara";
         s.Age = 9;
         Console.WriteLine("Student Info: {0}", s);
         
         //为age加1
         s.Age += 1;
         Console.WriteLine("Student Info: {0}", s);
         Console.ReadKey();
      }
   	}
	}
```

编译执行上述代码，得到如下结果：

```

    Student Info: Code = 001, Name = Zara, Age = 9
	Student Info: Code = 001, Name = Zara, Age = 10
```

## 抽象属性

抽象类可拥有抽象属性，这些属性应在派生类中被实现。下面的程序说明了这点：

```

    using System;
	namespace tutorialspoint
	{
   	public abstract class Person
   	{
      public abstract string Name
      {
         get;
         set;
      }
      public abstract int Age
      {
         get;
         set;
      }
   	}
   
   	class Student : Person
   	{ 
      private string code = "N.A";
      private string name = "N.A";
      private int age = 0;
      
      // 为字符类型声明一个叫Code的属性：
      public string Code
      {
         get
         {
            return code;
         }
         set
         {
            code = value;
         }
      }
      
      // 为字符类型声明一个叫Name的属性：
      public override string Name
      {
         get
         {
            return name;
         }
         set
         {
            name = value;
         }
      }
      
      // 为整形类型声明一个叫Age的属性：
      public override int Age
      {
         get
         {
            return age;
         }
         set
         {
            age = value;
         }
      }
      public override string ToString()
      {
         return "Code = " + Code +", Name = " + Name + ", Age = " + Age;
      }
   	}
   
   	class ExampleDemo
   	{
      public static void Main()
      {
         // 创建一个Student类的对象
         Student s = new Student();
         
         // 为student对象设置code，name和age
         s.Code = "001";
         s.Name = "Zara";
         s.Age = 9;
         Console.WriteLine("Student Info:- {0}", s);
         
         //为age加1
         s.Age += 1;
         Console.WriteLine("Student Info:- {0}", s);
         Console.ReadKey();
      }
   	}
	}
```

编译执行上述代码，得到如下结果：

```

    Student Info: Code = 001, Name = Zara, Age = 9
	Student Info: Code = 001, Name = Zara, Age = 10
```
