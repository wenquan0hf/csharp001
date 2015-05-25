# C# - 文件I/O

文件是存储在磁盘具有特定名称和目录路径的数据的集合。当一个文件被打开阅读或书写时，就变成了流。

流基本上是通过通信路径中的字节顺序。主要有两个流：输入流和输出流。输入流用于从文件系统中读取数据，输出流用于向文件中写数据。

## I/O类

System.IO 的命名空间有多种类，这些类被用于执行大量和文件有关的操作，例如创建和删除文件，读写文件，关闭文件等等。

下面的表格中列出了一些 System.IO 命名空间中常用的非抽象类：

| I/O 类        | 描述           |
| ------------- |:-------------:|
| BinaryReader      | 从二进制流读取原始数据 |
| BinaryWriter     | 以二进制形式写入原始数据     |
| BufferedStream | 字节流的临时存储      |
| Directory      | 用于操作目录结构 |
| DirectoryInfo      | 用于创建复合条件指令。      |
| DriveInfo | 用于执行目录操作      |
| File      | 用于操作文件 |
| FileInfo      | 用于执行文件操作     |
| FileStream | 用于读写文件中任意位置的内容      |
| MemoryStream      | 用于随机存取存储器中存储的流数据|
| Path      | 用于执行有关路径信息的操作      |
| StreamReader      | 用于从字节流中读取字符      |
| StreamWriter | 用于向流中写字符     |
| StringReader      | 用于读取字符串数组 |
| StringWriter      | 用于写入字符串数组      |

## FileStream 类

System.IO 命名空间中的FileStream类有助于读取，写入和关闭文件。这个类派生自抽象类流。

你需要创建一个 FileStream 对象用于创建一个新的文件或打开一个已存在的文件。创建 FileStream 对象的语法如下：

```

    FileStream <object_name> = new FileStream( <file_name>, <FileMode Enumerator>, <FileAccess Enumerator>, <FileShare Enumerator>);

```

例如，创建一个 FileStream 对象F，读取一个名为 sample.txt 的文件的方法如下：

```

    FileStream F = new FileStream("sample.txt", FileMode.Open, FileAccess.Read, FileShare.Read);

```

| 参数        | 描述           |
| ------------- |:-------------|
| FileMode      | fileMode枚举定义了各种方法来打开文件。fileMode枚举的成员是：<br>   * **Append**: 打开一个已有的文件，并将光标放置在文件的末尾。如果文件不存在，则创建文件。<br>   * **Create**: 它创建一个新的文件<br>   * **CreateNew**: 指定操作系统应创建一个新的文件。如果文件已存在，则抛出异常。<br>   * **Open**: 它会打开一个现有的文件<br>   * **OpenOrCreate**: 指定操作系统应打开一个已有的文件。如果文件不存在，则用指定的名称创建一个新的文件打开。<br>   * **Truncate**: 打开一个已有的文件，文件一旦打开，就将被截断为零字节大小。 |
| FileAccess      | FileAccess 枚举成员有：Read, ReadWrite 和 Write.     |
| FileShare | FileShare枚举有以下成员：<br>   * **Inheritable**: 允许文件句柄可由子进程继承。<br>   * **None**: 它拒绝共享当前文件<br>   * **Read**: 它允许打开文件进行读取<br>   * **ReadWrite**: 它允许打开文件进行读取和写入<br>   * **Write**: 它允许打开文件写入      |

##　例子

下面的程序示范了 FileStream 类：

```

    using System;
	using System.IO;

	namespace FileIOApplication
	{
   		class Program
   		{
      		static void Main(string[] args)
      		{
         		FileStream F = new FileStream("test.dat", FileMode.OpenOrCreate, FileAccess.ReadWrite);
         		for (int i = 1; i <= 20; i++)
         		{
         		   F.WriteByte((byte)i);
         		}
         
         		F.Position = 0;
         		for (int i = 0; i <= 20; i++)
         		{
            		Console.Write(F.ReadByte() + " ");
         		}
         		F.Close();
         		Console.ReadKey();
      		}
   		}
	}

```

编译执行上述代码，得到如下结果：

```

	1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 -1

```

## C# 中的高级文件操作

上面的实例演示了 C# 中简单的文件操作。但是，要充分利用 C# System.IO 类的强大功能，您需要知道这些类常用的属性和方法。

| 主题和描述        |
| ------------- |
| [文本文件的读写](http://www.tutorialspoint.com/csharp/csharp_text_files.htm)<br>它涉及到文本文件的读写。StreamReader 和 StreamWriter 类有助于完成文本文件的读写。      | 
| [二进制文件的读写](http://www.w3cschool.cc/csharp/csharp-binary-files.html) <br>它涉及到二进制文件的读写。BinaryReader 和 BinaryWriter 类有助于完成二进制文件的读写。     |
| [Windows文件系统的操作](http://www.w3cschool.cc/csharp/csharp-windows-file-system.html) <br>它让 C# 程序员能够浏览并定位 Windows 文件和目录。|
