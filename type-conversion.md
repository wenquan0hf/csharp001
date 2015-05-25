# C# 类型转换

类型转换从根本上说是类型铸造，或者说是把数据从一种类型转换为另一种类型。在 C# 中，类型铸造有两种形式：

- **隐式类型转换** 这些转换是 C# 默认的以安全方式进行的转换。例如，从小的整数类型转换为大的整数类型，从派生类转换为基类。
- **显式类型转换** 这些转换是通过用户使用预定义的函数显示完成的。显式转换需要强制转换运算符。
下面的实例显示了一个显式的类型转换：
```
namespace TypeConversionApplication
{
    class ExplicitConversion
    {
        static void Main(string[] args)
        {
            double d = 5673.74;
            int i;

            // 强制转换 double 为 int
            i = (int)d;
            Console.WriteLine(i);
            Console.ReadKey();
            
        }
    }
}
```
编译执行上述代码，得到如下结果：
```
5673
```
## C# 类型转换方法

C# 提供了下列内置的类型转换方法：

| 序号 | 方法 & 描述 |
| :--- | :--- |
|1|	ToBoolean <br>如果可能的话，把类型转换为布尔型。|
|2|	ToByte <br>把类型转换为字节类型。|
|3|	ToChar <br>如果可能的话，把类型转换为单个 Unicode 字符类型。|
|4|	ToDateTime <br>把类型（整数或字符串类型）转换为 日期-时间 结构。|
|5|	ToDecimal <br>把浮点型或整数类型转换为十进制类型。|
|6|	ToDouble <br>把类型转换为双精度浮点型。|
|7|	ToInt16 <br>把类型转换为 16 位整数类型。|
|8|	ToInt32 <br>把类型转换为 32 位整数类型。|
|9|	ToInt64 <br>把类型转换为 64 位整数类型。|
|10|	ToSbyte <br>把类型转换为有符号字节类型。|
|11|	ToSingle <br>把类型转换为小浮点数类型。|
|12|	ToString <br>把类型转换为字符串类型。|
|13|	ToType <br>把类型转换为指定类型。|
|14|	ToUInt16 <br>把类型转换为 16 位无符号整数类型。|
|15|	ToUInt32 <br>把类型转换为 32 位无符号整数类型。|
|16|	ToUInt64 <br>把类型转换为 64 位无符号整数类型。|

下面的实例把不同值类型变量转换为字符串类型变量：
```
namespace TypeConversionApplication
{
    class StringConversion
    {
        static void Main(string[] args)
        {
            int i = 75;
            float f = 53.005f;
            double d = 2345.7652;
            bool b = true;

            Console.WriteLine(i.ToString());
            Console.WriteLine(f.ToString());
            Console.WriteLine(d.ToString());
            Console.WriteLine(b.ToString());
            Console.ReadKey();
            
        }
    }
}
```
编译执行上述代码，得到如下结果：
```
75
53.005
2345.7652
True
```
