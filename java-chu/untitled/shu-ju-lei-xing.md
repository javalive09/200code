# 数据类型

## 基本数据类型（4类8种，能自动装箱）

**整形**

**byte（8 bit，1个字节 -128~127）**

存储和传输容量的计量单位，字节。最早的PC机数据总线宽度是8（8根线）用8位表示一个字（c中char是一个字节） 表示方法1：byte b = 1; 注意：默认类型是int型，所以当b在\[-128,127\]之间时编译器不会报错。 例如：byte a = 1；byte b = 2；byte c； c = a + 1; //会报错，相当于把int赋值给byte c = a + b //会报错，相当于把int赋值给byte short （16 bit， 2个字节） short a = 1; int b = a;//编译报错 注意：不可以显示的将范围大的数据类型赋值给范围小的数据类型 总结：可以将范围小的值赋给表示范围大的变量；但不能将表示范围大的值赋给表示范围小的变量，只能通过强制类型转换 范围大的强转成范围小的变量时：前面舍位 范围小的强转成范围大的变量时：前面补位 ,如是正数前面补位0，如是负数前面补位1.

**short（16 bit， 2个字节）**

short a = 1; int b = a;//编译报错 注意：不可以显示的将范围大的数据类型赋值给范围小的数据类型 总结：可以将范围小的值赋给表示范围大的变量；但不能将表示范围大的值赋给表示范围小的变量，只能通过强制类型转换 范围大的强转成范围小的变量时：前面舍位 范围小的强转成范围大的变量时：前面补位 ,如是正数前面补位0，如是负数前面补位1.

**int（32 bit，4个字节）**

整形的默认类型 表示方法: int i = 1;

**long（64 bit，8个字节）**

表示方法1： long m = 1; 表示方法2： long m = 2l; 表示方法3： long m = 2L;

**浮点型**

**float（32bit， 4个字节）**

表示方法1：float f = 11.11f; 表示方法2：float f = 11.11F;

**double（64bit，8个字节 ）**

浮点型的默认类型 表示方法1：double d = 11.11; 表示方法2：double d = 11.11D; 表示方法3：double d = 11.11d;

**字符型**

**char（16 bit， 2个字节）**

表示方法1：char c = ‘c’;表示一个字符 表示方法2：char c = 56;表示一个整数

**布尔型**

**boolean（1 bit）**

为了纪念英国数学家Boole-George，在逻辑运算（与或非，因果关系的运算）中有突出贡献 表示方法： boolean b =true/false;

**强制转换**

**正数**

小范围 --&gt; 大范围 ： 前面空位补0 大范围 --&gt; 小范围 ： 前面空位去0

**负数**

小范围 --&gt; 大范围 ： 前面空位补1 大范围 --&gt; 小范围 ： 前面空位去1

**十六进制字符串转换成int方法**

有时候编写color 相关 的程序时，需要将十六进制字符串转换成int。 String str = "0xC0A80010";  
Integer ss = 0xC0A80010;  
Long longStr = Long.parseLong\(str.substring\(2\), 16\);  
ss = longStr.intValue\(\);  
System.out.println\(ss\);  
System.out.println\(Integer.toHexString\(ss\)\); 打印结果：  
-1062731760 c0a80010

#### 引用数据类型

**类（class）**

**包装类（能自动拆箱）**

Byte，Short， Integer（自动装箱时 ，integer有一个缓存，介于-128~127之间的整数装箱时会用缓存的内容，超过范围会生成新的对象，所以比较integer时要注意 integer == integer） Long，Float，Double，Character，Boolean

**枚举类**

枚举每个元素都是该类的实例 枚举元素必须位于枚举类最开始 枚举只有一个成员时，可以作为一种单例实现形式

**其他类**

**接口（interface）**

#### String字符串

String的本质是char数组 private final char value\[\]; 默认数组长度是0

**StringBuilder**

线程不安全 本质是char数组 char\[\]value 默认数组长度是16 增长时int newCapacity =value.length \* 2 + 2;

**StringBuffer**

线程安全 char\[\]value 默认数组长度是16 增长时int newCapacity = value.length \* 2 + 2;

**String占用字节数**

Char c = “我”;//占用2个byte字节 String str = “我”； byte \[\] bytes = str.getByte\(\); byte长度是3而不是2 因为str.getBytes（encoding）是获取指定编码的byte数组，通常GBK是2个字节，utf-8是3个字节。如果不指定，则去默认的encoding。

**关于分隔**

StringTokenizer（字符串分隔解析器，默认分隔符：空格、回车、Tab） Token被分隔字符串中的一块，两端有分隔符

**对象个数**

String在方法区中有一个字符串池（常量）。每次都会在池中搜寻一次。 Stringa = “abc”; 如果池中有，则直接用池中的，如果没有在池中新建一个 所以String a = new String（“abc”）；会建立两个对象。

#### 面试题

**int 和 Integer 有什么区别？**

Int是Java的原始数据类型，Integer是java为int提供的封装类。

**short s1 = 1; s1 = s1 + 1;有什么错?**

s1+1运算结果是int型，需要强制转换类型。

**char型变量中能不能存贮一个中文汉字?**

在C语言中，char类型占1一个字节，而汉子占2个字节，所以不能存储。 在Java中，char类型占2个字节，而且Java默认采用Unicode编码，以个Unicode码是16位，所以一个Unicode码占两个字节，Java中无论汉字还是英文字母都是用Unicode编码来表示的。所以，在Java中，char类型变量可以存储一个中文汉字。

**Java支持的数据类型有哪些？什么是自动拆装箱？**

Java语言支持的8中基本数据类型是：byte short int long float double boolean char 自动装箱是Java编译器在基本数据类型和对应的对象包装类型之间做的一个转化。比如：把int转化成Integer，double转化成double，等等。反之就是自动拆箱。

