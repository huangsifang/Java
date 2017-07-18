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

