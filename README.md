Java优点：
编译器生成字节码文件，Java字节码文件被Java虚拟机（JVM）解释执行，可以在不同的硬件平台和操作系统上运行，解释Java字节码方式：翻译一步执行一步

编译：javac Welcome.java，生成.class字节码文件
运行：java Welcome（不能加扩展名.class）

NoClassDefFoundError错误：要运行的类不存在
NoSuchMethodError错误：类文件中没有main方法

类加载器：将类的字节码加载到内存中
字节码验证器：检验字节码的合法性

行注释  //
块注释  /*
？  java特殊注释  /**XXX*/  能使用JDK的javadoc命令提取成一个HTML文件

Cramer规则:
ax + by = e
cs + dy = f
x = (ed-bf)/(ad-bc)
y = (af-ec)/(ad-bc)

byte表示变量范围（-128~127）
表示一个long型的整型变量（2147483648L）
表示float类型（10.2f或10.2F）
表示double类型（10.2d或10.2D），默认为double类型
表示二进制  0b或0B
表示八进制  0
表示十六进制  0x或0X
为了提高可读性，允许使用下划线long a = 1111_2222_3333

System.currentTimeMillis()表示当前时间（从GMT1970年1月1日00:00:00开始到当前时刻的毫秒数）
totalSeconds = System.currentTimeMillis()/1000
秒：totalSeconds%60
totalMinutes = totalSeconds/60
分：totalMinutes%60
totalHours = totalMinutes/60
时：totalHours%24
可以使用System.currentTimeMillis()产生随机数

int sum = 0;
sum += 4.5  等价于  sum = (int)(sum+4.5)
结果sum==4
x1 op= x2 形式等价于  x1 = (T)(x1 op x2)，其中T是x1的类型

(int)(x*100)/100.0  显示小数点后两位

boolean b = true;
int a = (int)b;//编译错误
int i = 1;
boolean j = (boolean)i;//编译错误

判断浮点值相等：
final double EPSILON = IE-14;
Math.abs(x-0.5)<EPSILON

随机数：Math.random()  [0.0,1.0)
[1,100]  (int)(Math.random()*100+1)  int只保留整数部分

三角函数方法
sin(radians)  asin()
cos()  acos()
tan()  atan()
toRadians(degree)  将度转化为弧度
toDegrees(radians)  将弧度转化为度

指数函数方法：
exp(x)  e的x次方
pow(a, b)  a的b次方
log(x)  logx
log10(x)
sqrt(x)  x的平方根

取整方法：
Math.ceil(x)  向上取整  Math.ceil(2.1) = 3.0
Math.floor(x)  向下取整  Math.floor(2.9) = 2.0
Math.rint(x)  最接近整数，如果x与两个整数的距离相等，偶数的整数返回
Math.rint(2.5) = 2;  Math.rint(3.5) = 4;
Math.round(x)  四舍五入
若x为float类型，返回(int)Math.floor(x+0.5)
若x为double类型，返回(long)Math.floor(x+0.5)

Math.max(x)
Math.min(x)
Math.abs(x)

String
s.length()
s.charAt(index)
s.concat(sl)  字符串连接
s.toUpperCase()
s.toLowerCase()
s.trim()

比较：
s.equals(s1)
s.equalsIgnoreCase(s1)  不区分大小写
s.compareTo(s1)  返回大于0、等于0、小于0的整数，表示s>s1,s==s1,s<s1
s.compareIgnoreCase(s1)  不区分大小写
s.startsWith(prefix)  是否以特定的前缀开始
s.endsWith(prefix)  是否以特定的后缀结束
s.contains(s1)  s1是否是s的子字符串

截取：
s.subString(beginIndex)  从beginIndex（包括）到结束
s.subString(beginIndex, endIndex)  从beginIndex（包括）到endIndex-1，不包括endIndex

s.indexOf(ch)  返回第一个字符ch的下标，若没找到，返回-1
s.indexOf(ch, fromIndex)  从fromIndex开始找
s.indexOf(s1)  第一个字符串s1的下标
s.indexOf(s1, formIndex)
s.lastIndexOf(ch)
s.lastIndexOf(ch, fromIndex)
s.lastIndexOf(s)
s.lastIndexOf(s, formIndex)
例子：int k = s.indexOf(' ');
String firstName = s.subString(0, k);
String lastName = s.subString(k+1);

字符串转数字
Integer.parseInt(s)
Double.parseDouble(s)
数字转字符串
a+""

输入重定向：（程序从文件中读取输入）
java SentineValue < input.txt
输入重定向：（输出到文件中）
java ClassName > output.txt
合并
java SentinelValue <input.txt> output.txt
使用cmd命令行时需要先删去package XXX;，并先进行编译
编译：javac XXX.java 
执行：java XXX <input.txt> output.txt

由于精度问题，较大数+较小数可能不会改变
如10000000000.0+0.000000000001 = 10000000000.0
所以在较大数之前先增加较小数是减小误差的一种方法


