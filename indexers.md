# C\# 索引器
创建**索引器**可以使一个对象像数组一样被索引。为类定义索引器时，该类的行为类似于一个**虚拟数组**，使用数组访问运算符([ ])则可以对该类来进行访问。

## 句法规则
创建一个一维索引器的规则如下：

```
element-type this[int index]
{
   // The get accessor.
   get
   {
      // return the value specified by index
   }
   
   // The set accessor.
   set
   {
      // set the value specified by index
   }
}
```
## 使用索引器
索引器的声明在某种程度上类似于属性的声明，例如，使用 **get** 和 **set** 方法来定义一个索引器。不同的是，属性值的定义要求返回或设置一个特定的数据成员，而索引器的定义要求返回或设置的是某个对象实例的一个值，即索引器将实例数据切分成许多部分，然后通过一些方法去索引、获取或是设置每个部分。

定义属性需要提供属性名，而定义索引器需要提供一个指向对象实例的 **this** 关键字。

示例：

```
using System;
namespace IndexerApplication
{
   class IndexedNames
   {
      private string[] namelist = new string[size];
      static public int size = 10;
      public IndexedNames()
      {
         for (int i = 0; i < size; i++)
         namelist[i] = "N. A.";
      }
      
      public string this[int index]
      {
         get
         {
            string tmp;
         
            if( index >= 0 && index <= size-1 )
            {
               tmp = namelist[index];
            }
            else
            {
               tmp = "";
            }
            
            return ( tmp );
         }
         set
         {
            if( index >= 0 && index <= size-1 )
            {
               namelist[index] = value;
            }
         }
      }
      
      static void Main(string[] args)
      {
         IndexedNames names = new IndexedNames();
         names[0] = "Zara";
         names[1] = "Riz";
         names[2] = "Nuha";
         names[3] = "Asif";
         names[4] = "Davinder";
         names[5] = "Sunil";
         names[6] = "Rubic";
         for ( int i = 0; i < IndexedNames.size; i++ )
         {
            Console.WriteLine(names[i]);
         }
         
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Zara
Riz
Nuha
Asif
Davinder
Sunil
Rubic
N. A.
N. A.
N. A.
```
## 重载索引器
索引器允许重载，即允许使用多种不同类型的参数来声明索引器。索引值可以是整数，但也可以是其他的数据类型，如字符型。

重载索引器示例：

```
using System;
namespace IndexerApplication
{
   class IndexedNames
   {
      private string[] namelist = new string[size];
      static public int size = 10;
      public IndexedNames()
      {
         for (int i = 0; i < size; i++)
         {
            namelist[i] = "N. A.";
         }
      }
      
      public string this[int index]
      {
         get
         {
            string tmp;
            
            if( index >= 0 && index <= size-1 )
            {
               tmp = namelist[index];
            }
            else
            {
               tmp = "";
            }
            
            return ( tmp );
         }
         set
         {
            if( index >= 0 && index <= size-1 )
            {
               namelist[index] = value;
            }
         }
      }
      public int this[string name]
      {
         get
         {
            int index = 0;
            while(index < size)
            {
               if (namelist[index] == name)
               {
                return index;
               }
               index++;
            }
            return index;
         }

      }

      static void Main(string[] args)
      {
         IndexedNames names = new IndexedNames();
         names[0] = "Zara";
         names[1] = "Riz";
         names[2] = "Nuha";
         names[3] = "Asif";
         names[4] = "Davinder";
         names[5] = "Sunil";
         names[6] = "Rubic";
         
         //using the first indexer with int parameter
         for (int i = 0; i < IndexedNames.size; i++)
         {
            Console.WriteLine(names[i]);
         }
         
         //using the second indexer with the string parameter
         Console.WriteLine(names["Nuha"]);
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Zara
Riz
Nuha
Asif
Davinder
Sunil
Rubic
N. A.
N. A.
N. A.
2
```
