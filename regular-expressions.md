# C# - 正则表达式

正则表达式是一种可以和输入文本相匹配的表达式。.Net framework 提供了一个正则表达式引擎让这种匹配成为可能。一个表达式可以由一个或多个字符，运算符，或结构体组成。


## 构建正则表达式的定义

有很多种类的字符，运算符，结构体可以定义正则表达式。点击下面的连接查找这些结构：

* **[转义字符](http://www.tutorialspoint.com/csharp/csharp_character_escapes.htm)**
* **[字符类](http://www.tutorialspoint.com/csharp/csharp_character_classes.htm)**
* **[集合](http://www.tutorialspoint.com/csharp/csharp_anchors.htm)**
* **[分组构造](http://www.tutorialspoint.com/csharp/csharp_grouping_constructs.htm)**
* **[限定符](http://www.tutorialspoint.com/csharp/csharp_quantifiers.htm)**
* **[回溯引用构造](http://www.tutorialspoint.com/csharp/csharp_backreference_constructs.htm)**
* **[可替换结构](http://www.tutorialspoint.com/csharp/csharp_alternation_constructs.htm)**
* **[替换](http://www.tutorialspoint.com/csharp/csharp_substitutions.htm)**
* **[混合结构](http://www.tutorialspoint.com/csharp/csharp_miscellaneous_constructs.htm)**

##　**Regex** 正则表达式类

Regex 类用于表示一个正则表达式。它有下列常用的方法：

| Sr.No        | 方法           |
| ------------- |:-------------|
| 1      | public bool IsMatch(string input)<br>指出输入的字符串中是否含有特定的正则表达式。 |
| 2      | public bool IsMatch(string input, int startat)<br>指出输入的字符串中是否含有特定的正则表达式，该函数的 startat 变量指出了字符串开始查找的位置。     |
| 3 | public static bool IsMatch(string input, string pattern)<br>指出特定的表达式是否和输入的字符串匹配。      |
| 4      | public MatchCollection Matches(string input)<br>在所有出现的正则表达式中搜索特定的输入字符 |
| 5      | public string Replace(string input, string replacement)<br>在一个特定的输入字符中，用特定的字符串替换所有满足某个表达式的字符串。      |
| 6 | public string[] Split(string input)<br>将一个输入字符拆分成一组子字符串，从一个由正则表达式指出的位置上开始。     |



有关属性和方法的完成列表，请参见微软的 C# 文档。

## Example1

下列的例子中找出了以 s 开头的单词：

```
	using System;
	using System.Text.RegularExpressions;

	namespace RegExApplication
	{
   		class Program
  	 	{
      		private static void showMatch(string text, string expr)
      		{
         		Console.WriteLine("The Expression: " + expr);
         		MatchCollection mc = Regex.Matches(text, expr);
         		foreach (Match m in mc)
         		{
            		Console.WriteLine(m);
         		}
      		}
      
      		static void Main(string[] args)
      		{
         		string str = "A Thousand Splendid Suns";
         
         		Console.WriteLine("Matching words that start with 'S': ");
         		showMatch(str, @"\bS\S*");
         		Console.ReadKey();
      		}
   		}
	}	

```

编译执行上述代码，得到如下结果：

```

	Matching words that start with 'S':
	The Expression: \bS\S*
	Splendid
	Suns
```


## Example2

下面的例子中找出了以 m 开头以 e 结尾的单词

```

	using System;
	using System.Text.RegularExpressions;

	namespace RegExApplication
	{
   		class Program
   		{
      		private static void showMatch(string text, string expr)
      		{
         		Console.WriteLine("The Expression: " + expr);
         		MatchCollection mc = Regex.Matches(text, expr);
         		foreach (Match m in mc)
         		{
            		Console.WriteLine(m);
         		}
      		}
      		static void Main(string[] args)
     	 	{
         		string str = "make maze and manage to measure it";

         		Console.WriteLine("Matching words start with 'm' and ends with 'e':");
         		showMatch(str, @"\bm\S*e\b");
         		Console.ReadKey();
      		}
   		}
	}
```

编译执行上述代码，得到如下结果：

```

	Matching words start with 'm' and ends with 'e':
	The Expression: \bm\S*e\b
	make
	maze
	manage
	measure
```

## Example3

这个例子替换了额外的空白符：

```

	using System;
	using System.Text.RegularExpressions;

	namespace RegExApplication
	{
   		class Program
   		{
      		static void Main(string[] args)
      		{
         		string input = "Hello   World   ";
         		string pattern = "\\s+";
         		string replacement = " ";
         		Regex rgx = new Regex(pattern);
         		string result = rgx.Replace(input, replacement);

         		Console.WriteLine("Original String: {0}", input);
         		Console.WriteLine("Replacement String: {0}", result);    
         		Console.ReadKey();
      		}
   		}
	}

```

编译执行上述代码，得到如下结果：

```

	Original String: Hello World   
	Replacement String: Hello World

```
