# C\# -接口
  
一个接口定义为一种句法的合同，所有类继承接口应遵循。这个接口定义了部分的句法合同**“是什么（what）”**和派生类定义了部分的句法合同**“怎么做（how）”**。
  
接口定义的属性，方法和事件，是接口的成员。接口只包含成员的声明。它是派生类定义的成员的责任。它有助于提供一个派生类可以采用的标准的结构。
 
抽象类在一定程度上服务于同一目的，然而，它们大多被用于只由基类声明几个方法和派生类实现这些功能。
  
## 接口的声明
  
接口使用关键字 interface 声明。它类似于类的声明。接口声明缺省为 public 类型。以下是一个接口声明的例子：
<pre><code>public interface ITransactions
{
   // 接口成员
   void showTransaction();
   double getAmount();
}</code></pre>
  
## 示例
下面的示例演示上述接口的实现：
<pre><code>using System.Collections.Generic;
using System.Linq;
using System.Text;
using System;

namespace InterfaceApplication
{
   public interface ITransactions
   {
      // 接口成员
      void showTransaction();
      double getAmount();
   }
   
   public class Transaction : ITransactions
   {
      private string tCode;
      private string date;
      private double amount;
      public Transaction()
      {
         tCode = " ";
         date = " ";
         amount = 0.0;
      }
      
      public Transaction(string c, string d, double a)
      {
         tCode = c;
         date = d;
         amount = a;
      }
      
      public double getAmount()
      {
         return amount;
      }
      
      public void showTransaction()
      {
         Console.WriteLine("Transaction: {0}", tCode);
         Console.WriteLine("Date: {0}", date);
         Console.WriteLine("Amount: {0}", getAmount());
      }
   }
   class Tester
   {
      static void Main(string[] args)
      {
         Transaction t1 = new Transaction("001", "8/10/2012", 78900.00);
         Transaction t2 = new Transaction("002", "9/10/2012", 451900.00);
         t1.showTransaction();
         t2.showTransaction();
         Console.ReadKey();
      }
   }
}</code></pre>
编译执行上述代码，得到如下结果：
<pre><code>Transaction: 001
Date: 8/10/2012
Amount: 78900
Transaction: 002
Date: 9/10/2012
Amount: 451900</code></pre>

