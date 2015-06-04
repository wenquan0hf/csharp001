# 多线程

**线程**的定义是程序的执行路径。每个线程都定义了一个独特的控制流，如果应用程序涉及到复杂且耗时的操作，那么设置不同的线程执行路径会非常有好处，因为每个线程会被指定于执行特定的工作。

线程实际上是**轻量级进程**。一个常见的使用线程的实例是现代操作系统中的并行编程。使用线程不仅有效地减少了 CPU 周期的浪费，同时还提高了应用程序的运行效率。

到目前为止我们所编写的程序都是以一个单线程作为应用程序的运行的，其运行过程均为单一的。但是，在这种情况下，应用程序在同一时间只能执行一个任务。为了使应用程序可以同时执行多个任务，需要将其被划分为多个更小的线程。

## 线程的声明周期

线程的生命周期开始于对象的 System.Threading.Thread 类创建时，结束于线程被终止或是完成执行时。
下列各项为线程在生命周期中的各种状态：

- **未启动状态**：线程实例已被创建但 Start 方法仍未被调用时的状态。
- **就绪状态**：线程已准备好运行，正在等待 CPU 周期时的状态。
- **不可运行状态**：下面的几种情况下线程是不可运行的：
 - 已经调用 Sleep 方法
 - 已经调用 Wait 方法
 - 通过 I/O 操作阻塞
- **死亡状态**：线程已完成执行或已终止的状态。

## 主线程

在 C# 中，System.Threading.Thread 类用于线程的工作。它允许创建并访问多线程应用程序中的单个线程。进程中第一个被执行的线程称为主线程。

当 C# 程序开始执行时，会自动创建主线程。使用 **Thread** 类创建的线程被主线程的子线程调用。通过 Thread 类的 **CurrentThread** 属性可以访问线程。

下面的程序演示了主线程的执行：

```
using System;
using System.Threading;

namespace MultithreadingApplication
{
   class MainThreadProgram
   {
      static void Main(string[] args)
      {
         Thread th = Thread.CurrentThread;
         th.Name = "MainThread";
         Console.WriteLine("This is {0}", th.Name);
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
This is MainThread
```

## Thread 类的属性和方法

下表为 Thread 类一些常用的属性：

| 属性        | 描述          | 
| ------------- |:-------------|
| CurrentContext | 获取线程当前正在执行的线程的上下文。 |
| CurrentCulture | 获取或设置当前线程的区域性      |
| CurrentPrinciple| 获取或设置线程的当前责任人（针对基于角色的安全性）|
| CurrentThread|获取当前正在运行的线程 |
| CurrentUICulture|获取或设置资源管理器当前所使用的区域性，便于在运行时查找区域性特定的资源 |
| ExecutionContext|获取一个 ExcutionContext 对象，该对象包含有关当前线程的各种上下文信息。|
| IsAlive|获取一个值，指示当前线程的执行状态。 |
| IsBackground|获取或设置一个值，指示线程是否为后台线程。|
| IsThreadPoolThread|获取或设置一个值，指示线程是否属于托管线程池。|
| ManagedThreadId|获取当前托管线程的唯一标识符|
| Name|获取或设置线程的名称。 |
| Priority|获取或设置一个值，指示线程的调度优先级 |
| ThreadState|获取一个值，指示当前线程的状态。 |

下表为 Thread 类一些常用的方法：

| 序号      | 方法名和描述          | 
| ------------- |:-------------|
| 1| **public void Abort()** </br>在调用此方法的线程上引发 ThreadAbortException，则触发终止此线程的操作。调用此方法通常会终止线程。 |
| 2| **public static LocalDataStoreSlot AllocateDataSlot()** </br>在所有的线程上分配未命名的数据槽。使用以 ThreadStaticAttribute 属性标记的字段，可获得更好的性能。|
| 3| **public static LocalDataStoreSlot AllocateNamedDataSlot( string name)** </br>在所有线程上分配已命名的数据槽。使用以 ThreadStaticAttribute 属性标记的字段，可获得更好的性能。|
| 4|**public static void BeginCriticalRegion()** </br>通知主机将要进入一个代码区域，若该代码区域内的线程终止或发生未经处理的异常，可能会危害应用程序域中的其他任务。|
| 5|**public static void BeginThreadAffinity()** </br>通知主机托管代码将要执行依赖于当前物理操作系统线程的标识的指令。|
| 6|**public static void EndCriticalRegion()** </br>通知主机将要进入一个代码区域，若该代码区域内的线程终止或发送未经处理的异常，仅会影响当前任务。|
| 7|**public static void EndThreadAffinity()** </br>通知主机托管代码已执行完依赖于当前物理操作系统线程的标识的指令。|
| 8|**public static void FreeNamedDataSlot(string name)** </br>消除进程中所有线程的名称与槽之间的关联。使用以 ThreadStaticAttribute 属性标记的字段，可获得更好的性能。|
| 9|**public static Object GetData( LocalDataStoreSlot slot )** </br>在当前线程的当前域中从当前线程上指定的槽中检索值。使用以 ThreadStaticAttribute 属性标记的字段，可获得更好的性能。|
| 10|**public static AppDomain GetDomain()** </br>返回当前线程正在其中运行的当前域。|
| 11|**public static AppDomain GetDomainID()** </br>返回唯一的应用程序域标识符。 |
| 12|**public static LocalDataStoreSlot GetNamedDataSlot( string name )** </br>查找已命名的数据槽。使用以 ThreadStaticAttribute 属性标记的字段，可获得更好的性能。|
| 13|**public void Interrupt()** </br>中断处于 WaitSleepJoin 线程状态的线程。|
| 14|**public void Join()** </br>在继续执行标准的 COM 和 SendMessage 消息泵处理期间，阻塞调用线程，直到某个线程终止为止。此方法有不同的重载形式。|
| 15|**public static void MemoryBarrier()** </br>按如下方式同步内存存取：执行当前线程的处理器在对指令进行重新排序时，不能采用先执行 MemoryBarrier 调用之后的内存存取，再执行 MemoryBarrier 调用之前的内存存取的方式。|
| 16|**public static void ResetAbort()** </br>取消当前线程请求的 Abort 操作。|
| 17|**public static void SetData( LocalDataStoreSlot slot, Object data )** </br>在指定槽中，设置当前正在运行中线程的当前域的数据。使用以 ThreadStaticAttribute 属性标记的字段，可获得更好的性能。|
| 18|**public void Start()** </br>开始一个线程。|
| 19|**public static void Sleep( int millisecondsTimeout )** </br>令线程暂停一段时间。|
| 20|**public static void SpinWait( int iterations )** </br>令线程等待一段时间，时间长度由 iterations 参数定义。|
| 21|**public static byte VolatileRead( ref byte address )；public static double VolatileRead( ref double address )；public static int VolatileRead( ref int address )；public static Object VolatileRead( ref Object address )**  </br>读取字段的值。无论处理器的数目或处理器缓存的状态如何，该值都表示由计算机中任何一个处理器写入的最新值。此方法有不同的重载形式，此处仅给出部分例子。|
| 22|**public static void VolatileWrite( ref byte address, byte value )；public static void VolatileWrite( ref double address, double value )；public static void VolatileWrite( ref int address, int value )；public static void VolatileWrite( ref Object address, Object value )** </br>立即写入一个值到字段中，使该值对计算机中的所有处理器都可见。此方法有不同的重载形式，此处仅给出部分例子。|
| 23|**public static bool Yield()** </br>令调用线程执行已准备好在当前处理器上运行的另一个线程，由操作系统选择要执行的线程。|

## 线程的创建

线程是通过扩展 Thread 类创建的，扩展而来的 Thread 类调用 **Start()** 方法即可开始子线程的执行。
示例：

```
using System;
using System.Threading;

namespace MultithreadingApplication
{
   class ThreadCreationProgram
   {
      public static void CallToChildThread()
      {
         Console.WriteLine("Child thread starts");
      }
      
      static void Main(string[] args)
      {
         ThreadStart childref = new ThreadStart(CallToChildThread);
         Console.WriteLine("In Main: Creating the Child thread");
         Thread childThread = new Thread(childref);
         childThread.Start();
         Console.ReadKey();
      }
   }
}

```

编译执行上述代码段，得到如下结果：

```
In Main: Creating the Child thread
Child thread starts
```

## 线程的管理

Thread 类提供了多种用于线程管理的方法。
下面的示例调用了 **sleep()** 方法来在一段特定时间内暂停线程：

```
using System;
using System.Threading;

namespace MultithreadingApplication
{
   class ThreadCreationProgram
   {
      public static void CallToChildThread()
      {
         Console.WriteLine("Child thread starts");
         
         // 令线程暂停 5000 毫秒
         int sleepfor = 5000; 
         
         Console.WriteLine("Child Thread Paused for {0} seconds", sleepfor / 1000);
         Thread.Sleep(sleepfor);
         Console.WriteLine("Child thread resumes");
      }
      
      static void Main(string[] args)
      {
         ThreadStart childref = new ThreadStart(CallToChildThread);
         Console.WriteLine("In Main: Creating the Child thread");
         Thread childThread = new Thread(childref);
         childThread.Start();
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下代码段：

```
In Main: Creating the Child thread
Child thread starts
Child Thread Paused for 5 seconds
Child thread resumes
```

## 线程的销毁

使用 **Abort()** 方法可销毁线程。

在运行时，通过抛出 **ThreadAbortException** 来终止线程。这个异常无法被捕获，当且仅当具备 *finally* 块时，才将控制送到 *finally* 块中。

示例：

```
using System;
using System.Threading;

namespace MultithreadingApplication
{
   class ThreadCreationProgram
   {
      public static void CallToChildThread()
      {
         try
         {
            Console.WriteLine("Child thread starts");
            
            // 执行一些任务，如计十个数
            for (int counter = 0; counter <= 10; counter++)
            {
               Thread.Sleep(500);
               Console.WriteLine(counter);
            }
            
            Console.WriteLine("Child Thread Completed");
         }
         
         catch (ThreadAbortException e)
         {
            Console.WriteLine("Thread Abort Exception");
         }
         finally
         {
            Console.WriteLine("Couldn't catch the Thread Exception");
         }
      }
      
      static void Main(string[] args)
      {
         ThreadStart childref = new ThreadStart(CallToChildThread);
         Console.WriteLine("In Main: Creating the Child thread");
         Thread childThread = new Thread(childref);
         childThread.Start();
         
         // 将主线程停止一段时间
         Thread.Sleep(2000);
         
         // 中止子线程
         Console.WriteLine("In Main: Aborting the Child thread");
         
         childThread.Abort();
         Console.ReadKey();
      }
   }
}
```
编译执行上述代码，得到如下结果：

```
In Main: Creating the Child thread
Child thread starts
0
1
2
In Main: Aborting the Child thread
Thread Abort Exception
Couldn't catch the Thread Exception
```
