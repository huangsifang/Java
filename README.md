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
[0,100]  (int)(Math.random()*(100+1))  int只保留整数部分
[a,b]  (int)(Math.random()*(b-a+1))

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


数组：
对于char[]类型的数组，可以使用一条语句打印
char[] city = {'A', 'B', 'C'};
System.out.println(city);

for(double e:myList){ }  顺序遍历整个数组

复制数组
1.循环
2.System类中的静态方法arraycopy
arraycopy(sourceArray, srcPos, targetArray, tarPos, length)
从源数组sourceArray的srcPos下标处复制length个到目标数组targetArray的tarPos处
复制整个数组：arraycopy(sourceArray, 0, targetArray, 0, sourceArray.length)
3.clone方法

可变长参数：
public static void printMax(double... numbers) {}
其中numbers在该方法中相当于一个数组
使用方法：printMax(1.1, 3.2, 5, 6.1, 0);

二分查找：
public static int binarySearch(int[] list, int key) {
	int low = 0;
	int high = list.length-1;

	while(low<=high) {
		int mid = (low+high)/2;
		if(key < list[mid]) {
			high = mid-1;
		}
		else if(key == list[mid]) {
			return mid;
		}
		else {
			low = mide+1;
		}
	}
	return -1;
}
使用Arrays类
java.util.Arrays.binarySearch(list, 11);

数组排序：
java.util.Arrays.sort(array);
java.util.Arrays.sort(array, 1, 3);从array[1]到ayyay[3-1]部分数组排序
java.util.Arrays.parallelSort(array);
java.util.Arrays.parallelSort(array, 1, 3);
如果计算机有多个处理器，那么parallelSort更加高效

检测两个数组是否相等
java.util.Arrays.equals(list1, list2);

填满数组
java.util.Arrays.fill(list, 5);//用数值5填满list数组
java.util.Arrays.fill(list, 1, 5, 8);//用数值8填充到list[1]到list[5-1]中

数组返回字符串
Arrays.toString(list)

main方法可以从命令行接收字符串参数  main(String[] args)
java XXX "First num" alpha 123
arg = ["First num", "alpha", "123"];

二维数组：
int[][] triangleArray = new int[5][];//必须指定第一个下标
triangleArray[0] = new int[5];
...

引用类型的默认值是null
数值类型的默认值是0
boolean类型的默认值是false
char类型的默认值是'\u0000'
class Student {
	int x;
	public static void main(String[] args) {
		Student stu = new Student();
		System.out.println(stu.x); //0
	}
}
但是局部变量没有默认值
public static void main(String[] args) {
	int x;
	System.out.println(x); //错误
}

当不需要摸个对象时，将该对象的引用变量赋值null值

Date类：
getTime()  返回从1970年1月1日至今的时间
toString()  返回Mon Dec 26 07:43:39 EST 2011格式时间

Point2D类
Point2D p1 = new Point2D(x1, y1);
Point2D p2 = new Point2D(x2, y2);
p1.toString() //Point2D [x = 1, y = 1]
p1.distance(2,2) //p1到(2,2)之间的距离
p1.distance(p2) //p1到p2之间的距离
p1.getX()
p1.getY()

this调用隐藏数据域
public Circle(double radius) {
	this.radius = radius;
}
public Circle() {
	this(1.0); //调用另一个构造方法，在其他任何可执行的语句之前出现
}