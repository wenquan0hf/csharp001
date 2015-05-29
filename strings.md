# # C\# 字符串
在 C# 中，可以使用字符串作为字符数组，但更常见的做法是使用 string 关键字来声明一个字符串变量。该 string 关键字是 System.String 类的别名。
## 创建一个 String 对象
可以使用下列方法之一字符串对象：
- 通过指定一个字符串给一个字符串变量
- 通过使用 String 类的构造函数
- 通过使用字符串连接运算符(+)
- 通过检索属性或调用返回一个字符串的方法
- 通过调用格式化方法的值或对象转换成它的字符串表示
  
下面的例子说明了这一点：
```
using System;
namespace StringApplication
{
   class Program
   {
      static void Main(string[] args)
      {
         //from string literal and string concatenation
         string fname, lname;
         fname = "Rowan";
         lname = "Atkinson";
         
         string fullname = fname + lname;
         Console.WriteLine("Full Name: {0}", fullname);
         
         //by using string constructor
         char[] letters = { 'H', 'e', 'l', 'l','o' };
         string greetings = new string(letters);
         Console.WriteLine("Greetings: {0}", greetings);
         
         //methods returning string
         string[] sarray = { "Hello", "From", "Tutorials", "Point" };
         string message = String.Join(" ", sarray);
         Console.WriteLine("Message: {0}", message);
         
         //formatting method to convert a value
         DateTime waiting = new DateTime(2012, 10, 10, 17, 58, 1);
         string chat = String.Format("Message sent at {0:t} on {0:D}", waiting);
         Console.WriteLine("Message: {0}", chat);
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
Full Name: Rowan Atkinson
Greetings: Hello
Message: Hello From Tutorials Point
Message: Message sent at 5:58 PM on Wednesday, October 10, 2012
```
## String 类的属性
String 类有以下两个属性：

| 序号 |	属性名称和描述 |
| ------ | ------ |
| 1 |	Chars  获取在当前字符串对象中的指定位置的字符对象 |
| 2 |	Length  获取字符在当前字符串对象的数目 |

## String 类的方法
String 类有许多方法，以帮助使用 String 对象。下表提供了一些最常用的方法：

| 序号 |	属性名称和描述 |
| ------ | ------ |
| 1 |	**public static int Compare(string strA,string strB)**<br> 比较两个指定的字符串对象，并返回一个整数，指示其在排序顺序相对位置 |
| 2 |	**public static int Compare(string strA,string strB,bool ignoreCase)**<br>   比较两个指定的字符串对象，并返回一个整数，指示其在排序顺序相对位置。但是，它忽略情况下，如果布尔参数为true |
| 3 |	**public static string Concat(string str0,string str1)**<br>   连接两个字符串对象 |
| 4 | **public static string Concat(string str0,string str1,string str2)**<br>   拼接三个字符串对象 |
| 5 |	**public static string Concat(string str0,string str1,string str2,string str3)**<br>   符连接四个字符串对象 |
| 6 |	**public bool Contains(string value)**<br>  返回一个值，指示指定的字符串对象是否发生此字符串中 |
| 7 |	**public static string Copy(string str)**<br>  创建具有相同的值作为指定字符串的新String对象 |
| 8 |	**public void CopyTo(int sourceIndex,char[] destination,int destinationIndex,int count)**<br>  复制从字符串对象到指定位置Unicode字符数组的指定位置指定的字符数 |
| 9 | **public bool EndsWith(string value)**<br> 确定字符串对象的末尾是否与指定的字符串匹配 |
| 10 | **public bool Equals(string value)**<br> 确定当前字符串对象，并指定字符串对象是否具有相同的值 |
| 11 | **public static bool Equals(string a,string b)**<br> 确定两个指定的String对象是否具有相同的值 |
| 12 | **public static string Format(string format,Object arg0)**<br> 替换指定的字符串指定对象的字符串表示在一个或多个格式项 |
| 13 | **public int IndexOf(char value)**<br>返回当前字符串指定Unicode字符中第一次出现从零开始的索引 |
| 14 | **public int IndexOf(string value)**<br> 返回在这种情况下指定字符串中第一次出现从零开始的索引 |
| 15 | **public int IndexOf(char value,int startIndex)**<br> 返回此字符串指定Unicode字符中第一次出现从零开始的索引，搜索开始在指定的字符位置 |
| 16 | **public int IndexOf(string value,int startIndex)**<br> 返回在这种情况下指定字符串中第一次出现的从零开始的索引，搜索开始在指定的字符位置 |
| 17 |**public int IndexOfAny(char[] anyOf)**<br> 返回Unicode字符指定数组中第一次出现的任何字符的这个实例从零开始的索引 |
| 18 | **public int IndexOfAny(char[] anyOf,int startIndex)**<br> 返回Unicode字符指定数组，开始搜索从指定字符位置中第一次出现的任何字符的这个实例从零开始的索引 |
| 19 | **public string Insert(int startIndex,string value)**<br> 返回在指定的字符串被插入在当前字符串对象指定索引位置一个新的字符串 |
| 20 | **public static bool IsNullOrEmpty(string value)**<br> 指示指定的字符串是否为空或空字符串
| 21 | **public static string Join(string separator,params string[] value)**<br> 连接字符串数组中的所有元素，使用每个元件之间指定的分隔 |
| 22 | **public static string Join(string separator,string[] value,int startIndex,int count)**<br> 连接字符串数组的指定元素，利用每一个元素之间指定分隔符 |
| 23 | **public int LastIndexOf(char value)**<br> 返回当前字符串对象中指定的Unicode字符的最后出现从零开始的索引位置 |
| 24 | **public int LastIndexOf(string value)**<br> 返回当前字符串对象中的指定字符串最后一次出现的从零开始的索引位置 |
| 25 | **public string Remove(int startIndex)**<br> 删除在当前实例中的所有字符，开始在指定的位置，并继续通过最后位置，并返回字符串 |
| 26 | **public string Remove(int startIndex,int count)**<br> 删除在当前字符串的字符开始的指定位置的指定数量，并返回字符串 |
| 27 | **public string Replace(char oldChar,char newChar)**<br> 替换与指定的Unicode字符当前字符串对象指定的Unicode字符的所有匹配，并返回新的字符串 |
| 28 | **public string Replace(string oldValue,string newValue)**<br> 替换用指定的字符串当前字符串对象指定的字符串的所有匹配，并返回新的字符串 |
| 29 |**public string[] Split(params char[] separator)**<br> 返回一个字符串数组，其中包含的子字符串在当前字符串对象，由指定的Unicode字符数组的元素分隔 |
| 30 | **public string[] Split(char[] separator,int count)**<br> 返回一个字符串数组，其中包含的子字符串在当前字符串对象，由指定的Unicode字符数组的元素分隔。整型参数指定的子串返回最大数量 |
| 31 | **public bool StartsWith(string value)**<br>  确定此字符串实例的开头是否与指定的字符串匹配 |
| 32 | **public char[] ToCharArray()**<br> 返回一个Unicode字符数组，在当前字符串对象中的所有字符 |
| 33 | **public char[] ToCharArray(int startIndex,int length)**<br>  返回一个Unicode字符数组，在当前字符串对象中的所有字符，从指定的索引开始，并到指定的长度 |
| 34 | **public string ToLower()**<br> 返回此字符串的一个副本转换为小写 |
| 35 | **public string ToUpper()**<br> 返回此字符串的一个副本转换为大写 |
| 36 | **public string Trim()**<br> 从当前String对象去除所有开头和结尾的空白字符 |

方法上述名单并不是详尽的信息，请访问MSDN库的方法和String类的构造函数的完整列表。

示例:

下面的例子说明了一些上面提到的方法： 

**比较字符串：**
```
using System;
namespace StringApplication
{
   class StringProg
   {
      static void Main(string[] args)
      {
         string str1 = "This is test";
         string str2 = "This is text";

         if (String.Compare(str1, str2) == 0)
         {
            Console.WriteLine(str1 + " and " + str2 +  " are equal.");
         }
         else
         {
            Console.WriteLine(str1 + " and " + str2 + " are not equal.");
         }
         Console.ReadKey() ;
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
This is test and This is text are not equal.
```
**String包含字符串：**
```
using System;
namespace StringApplication
{
   class StringProg
   {
      static void Main(string[] args)
      {
         string str = "This is test";
         if (str.Contains("test"))
         {
            Console.WriteLine("The sequence 'test' was found.");
         }
         Console.ReadKey() ;
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
The sequence 'test' was found.
```
**获取一个子字符串：**
```
using System;
namespace StringApplication
{
   class StringProg
   {
      static void Main(string[] args)
      {
         string str = "Last night I dreamt of San Pedro";
         Console.WriteLine(str);
         string substr = str.Substring(23);
         Console.WriteLine(substr);
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
San Pedro
```
**连接字符串：**
```
using System;
namespace StringApplication
{
   class StringProg
   {
      static void Main(string[] args)
      {
         string[] starray = new string[]{"Down the way nights are dark",
         "And the sun shines daily on the mountain top",
         "I took a trip on a sailing ship",
         "And when I reached Jamaica",
         "I made a stop"};

         string str = String.Join("\n", starray);
         Console.WriteLine(str);
      }
   }
}
```
编译执行上述代码，得到如下结果：
```
Down the way nights are dark
And the sun shines daily on the mountain top
I took a trip on a sailing ship
And when I reached Jamaica
I made a stop
```
