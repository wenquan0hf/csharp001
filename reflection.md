# 反射

反射（Reflection） 对象用于在运行时获取类型信息。该类位于 System.Reflection 命名空间中，可访问一个正在运行的程序的元数据。

System.Reflection 命名空间包含了允许您获取有关应用程序信息及向应用程序动态添加类型、值和对象的类。

## 反射的应用

反射（Reflection）有下列用途：

- 它允许在运行时查看属性（attribute）信息。
- 它允许审查集合中的各种类型，以及实例化这些类型。
- 它允许延迟绑定的方法和属性（property）。
- 它允许在运行时创建新类型，然后使用这些类型执行一些任务。

## 查看元数据

我们已经在上面的章节中提到过，使用反射（Reflection）可以查看属性（attribute）信息。

System.Reflection 类的 MemberInfo 对象需要被初始化，用于发现与类相关的属性（attribute）。为了做到这点，您可以定义目标类的一个对象，如下：

```
    System.Reflection.MemberInfo info = typeof(MyClass);
```

下面的程序示范了这点：

```
    using System;

	[AttributeUsage(AttributeTargets.All)]
	public class HelpAttribute : System.Attribute
	{
   		public readonly string Url;
   
   		public string Topic   // Topic 是一个表示名字的参数
   		{
      		get
      		{
         		return topic;
      		}
      		set
      		{
         		topic = value;
      		}
  		}
   
   		public HelpAttribute(string url)   // url 是一个表示位置的参数
   		{
      		this.Url = url;
   		}
   		private string topic;
	}

	[HelpAttribute("Information on the class MyClass")]
	class MyClass
	{
	}
	namespace AttributeAppl
	{
   		class Program
   		{
      		static void Main(string[] args)
      		{
         		System.Reflection.MemberInfo info = typeof(MyClass);
         		object[] attributes = info.GetCustomAttributes(true);
         		for (int i = 0; i < attributes.Length; i++)
         		{
            		System.Console.WriteLine(attributes[i]);
         		}
         
         		Console.ReadKey();
      		}
   		}
	}
```

当上面的代码被编译和执行时，它会显示附加到类 MyClass 上的自定义属性：

```
    HelpAttribute
```

## 示例

在本实例中，我们将使用在上一章中创建的 DeBugInfo 属性，并使用反射（Reflection）来读取 Rectangle 类中的元数据。

```
    using System;
	using System.Reflection;

	namespace BugFixApplication
	{
   		//自定义特性BugFix分配给一个类和他的成员
   		[AttributeUsage(AttributeTargets.Class |
   		AttributeTargets.Constructor |
   		AttributeTargets.Field |
   		AttributeTargets.Method |
   		AttributeTargets.Property,
   		AllowMultiple = true)]

   		public class DeBugInfo : System.Attribute
   		{
      		private int bugNo;
      		private string developer;
      		private string lastReview;
      		public string message;
      
      	public DeBugInfo(int bg, string dev, string d)
      	{
         	this.bugNo = bg;
         	this.developer = dev;
         	this.lastReview = d;
      	}
      
      	public int BugNo
      	{
         	get
         	{
            	return bugNo;
         	}
      	}
      
      	public string Developer
      	{
         	get
         	{
            	return developer;
         	}
      	}
      
      public string LastReview
      {
         get
         {
            return lastReview;
         }
      }
      
      public string Message
      {
         get
         {
            return message;
         }
         set
         {
            message = value;
         }
      }
   	}
   	[DeBugInfo(45, "Zara Ali", "12/8/2012", Message = "Return type mismatch")]
   	[DeBugInfo(49, "Nuha Ali", "10/10/2012", Message = "Unused variable")]
   
   	class Rectangle
   	{
      //成员变量
      protected double length;
      protected double width;
      public Rectangle(double l, double w)
      {
         length = l;
         width = w;
      }
      [DeBugInfo(55, "Zara Ali", "19/10/2012", Message = "Return type mismatch")]
      public double GetArea()
      {
         return length * width;
      }
      [DeBugInfo(56, "Zara Ali", "19/10/2012")]
      public void Display()
      {
         Console.WriteLine("Length: {0}", length);
         Console.WriteLine("Width: {0}", width);
         Console.WriteLine("Area: {0}", GetArea());
      }
   	}//Rectangle 类的结束
   
   	class ExecuteRectangle
   	{
      static void Main(string[] args)
      {
         Rectangle r = new Rectangle(4.5, 7.5);
         r.Display();
         Type type = typeof(Rectangle);
         
         //遍历 Rectangle 类的属性
         foreach (Object attributes in type.GetCustomAttributes(false))
         {
            DeBugInfo dbi = (DeBugInfo)attributes;
            if (null != dbi)
            {
               Console.WriteLine("Bug no: {0}", dbi.BugNo);
               Console.WriteLine("Developer: {0}", dbi.Developer);
               Console.WriteLine("Last Reviewed: {0}", dbi.LastReview);
               Console.WriteLine("Remarks: {0}", dbi.Message);
            }
         }
         
         //遍历方法属性
         foreach (MethodInfo m in type.GetMethods())
         {
            foreach (Attribute a in m.GetCustomAttributes(true))
            {
               DeBugInfo dbi = (DeBugInfo)a;
               if (null != dbi)
               {
                  Console.WriteLine("Bug no: {0}, for Method: {1}", dbi.BugNo, m.Name);
                  Console.WriteLine("Developer: {0}", dbi.Developer);
                  Console.WriteLine("Last Reviewed: {0}", dbi.LastReview);
                  Console.WriteLine("Remarks: {0}", dbi.Message);
               }
            }
         }
         
         Console.ReadLine();
      	}
   	}
	}
```

编译执行上述代码，得到如下结果：

```
    Length: 4.5
	Width: 7.5
	Area: 33.75
	Bug No: 49
	Developer: Nuha Ali
	Last Reviewed: 10/10/2012
	Remarks: Unused variable
	Bug No: 45
	Developer: Zara Ali
	Last Reviewed: 12/8/2012
	Remarks: Return type mismatch
	Bug No: 55, for Method: GetArea
	Developer: Zara Ali
	Last Reviewed: 19/10/2012
	Remarks: Return type mismatch
	Bug No: 56, for Method: Display
	Developer: Zara Ali
	Last Reviewed: 19/10/2012
	Remarks: 
```
