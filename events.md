# C\# 事件
**事件**指一个用户操作，如按键、点击、移动鼠标等，也可以是系统生成的通知。当事件发生时，应用需要对其作出相应的反应，如中断。另外，事件也用于内部进程通信。

## 通过事件使用委托
事件生成于类的声明中，通过使用同一个类或其他类中的委托与事件处理程序关联。包含事件的类用于发布事件，称为**发布器**类。其他接受该事件的类称为**订阅器**类。事件使用的是发布-订阅（publisher-subscriber）模型。

**发布器**是一个定义了事件和委托的对象，此外还定义了事件和委托之间的联系。一个发布器类的对象调用这个事件，同时通知其他的对象。

**订阅器**是一个接受事件并提供事件处理程序的对象。在发布器类中的委托调用订阅器类中的方法（或事件处理程序）。

## 声明事件
在类中声明一个事件，首先需要声明该事件对应的委托类型。如：

```
public delegate void BoilerLogHandler(string status);
```
其次为使用 **event** 关键字来声明这个事件：

```
//基于上述委托定义事件
public event BoilerLogHandler BoilerEventLog;
```

上述代码段定义了一个名为 *BoilerLogHandler* 的委托以及一个名为 *BoilerEventLog* 的事件，该事件生成时会自动调用委托。

## 示例 1

```
using System;
namespace SimpleEvent
{
   using System;
   
   public class EventTest
   {
      private int value;
      public delegate void NumManipulationHandler();
      public event NumManipulationHandler ChangeNum;
      protected virtual void OnNumChanged()
      {
         if (ChangeNum != null)
         {
            ChangeNum();
         }
         else
         {
            Console.WriteLine("Event fired!");
         }
      }
      
      public EventTest(int n )
      {
         SetValue(n);
      }
      
      public void SetValue(int n)
      {
         if (value != n)
         {
            value = n;
            OnNumChanged();
         }
      }
   }
   
   public class MainClass
   {
      public static void Main()
      {
         EventTest e = new EventTest(5);
         e.SetValue(7);
         e.SetValue(11);
         Console.ReadKey();
      }
   }
}
```

编译执行上述代码，得到如下结果：

```
Event Fired!
Event Fired!
Event Fired!
```

## 示例 2
该示例为一个简单的应用程序，该程序用于热水锅炉系统故障排除。当维修工程师检查锅炉时，锅炉的温度、压力以及工程师所写的备注都会被自动记录到一个日志文件中。

```
using System;
using System.IO;

namespace BoilerEventAppl
{
   // boiler 类
   class Boiler
   {
      private int temp;
      private int pressure;
      public Boiler(int t, int p)
      {
         temp = t;
         pressure = p;
      }
      
      public int getTemp()
      {
         return temp;
      }
      
      public int getPressure()
      {
         return pressure;
      }
   }
   
   // 事件发布器
   class DelegateBoilerEvent
   {
      public delegate void BoilerLogHandler(string status);
      
      // 基于上述委托定义事件
      public event BoilerLogHandler BoilerEventLog;
      
      public void LogProcess()
      {
         string remarks = "O. K";
         Boiler b = new Boiler(100, 12);
         int t = b.getTemp();
         int p = b.getPressure();
         if(t > 150 || t < 80 || p < 12 || p > 15)
         {
            remarks = "Need Maintenance";
         }
         OnBoilerEventLog("Logging Info:\n");
         OnBoilerEventLog("Temparature " + t + "\nPressure: " + p);
         OnBoilerEventLog("\nMessage: " + remarks);
      }
      
      protected void OnBoilerEventLog(string message)
      {
         if (BoilerEventLog != null)
         {
            BoilerEventLog(message);
         }
      }
   }
   
   // 该类保留写入日志文件的条款
   class BoilerInfoLogger
   {
      FileStream fs;
      StreamWriter sw;
      public BoilerInfoLogger(string filename)
      {
         fs = new FileStream(filename, FileMode.Append, FileAccess.Write);
         sw = new StreamWriter(fs);
      }
      
      public void Logger(string info)
      {
         sw.WriteLine(info);
      }
      
      public void Close()
      {
         sw.Close();
         fs.Close();
      }
   }
   
   // 事件订阅器
   public class RecordBoilerInfo
   {
      static void Logger(string info)
      {
         Console.WriteLine(info);
      }//end of Logger

      static void Main(string[] args)
      {
         BoilerInfoLogger filelog = new BoilerInfoLogger("e:\\boiler.txt");
         DelegateBoilerEvent boilerEvent = new DelegateBoilerEvent();
         boilerEvent.BoilerEventLog += new 
         DelegateBoilerEvent.BoilerLogHandler(Logger);
         boilerEvent.BoilerEventLog += new 
         DelegateBoilerEvent.BoilerLogHandler(filelog.Logger);
         boilerEvent.LogProcess();
         Console.ReadLine();
         filelog.Close();
      }//end of main

   }//end of RecordBoilerInfo
}
```

编译执行上述代码，得到如下结果：

```
Logging info:

Temperature 100
Pressure 12

Message: O. K
```
