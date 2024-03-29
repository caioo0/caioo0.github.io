# 第2章 变量和基本类型

>  **本笔记为《C++ Primer 中文版（第五版）》和 《C++ Primer （第五版）习题集》 第2章阅读要点总结，重要知识点归档以及练习题的解答，原书更为详细，笔记仅作学习交流使用，未经授权禁止转载。**

C++定义了几种基本内置类型，如字符、整型、浮点数等。

## 2.1 基本内置类型

基本内置类型包括 算数类型(arithmetic type)  和 空类型(void)。
- 算数类型包括字符、整型数、浮点数和布尔值。
- 空类型不对应具体的值。

### **2.1.1 算术类型**

分为**整型**(integral type)和**浮点型**

算术类型 C++ 标准下尺寸最小值 

![image-20230924102424649](.\img\image-20230924102424649.png)

**字符类型：**

1. char：1字节(byte)=8bit。
2. wchar_t：宽字符，用于扩展字符集，wchar_t 确保可以存放机器最大扩展字符集中的任意一个字符。
3. char16_t 和 char32_t：为 Unicode 字符集服务。

**注意：**不同系统会有所差异，1字节为 8 位。

**注意：**默认情况下，int、short、long都是带符号的，即 signed。

**注意：**long int 8 个字节，int 都是 4 个字节，早期的 C 编译器定义了 long int 占用 4 个字节，int 占用 2 个字节，新版的 C/C++ 标准兼容了早期的这一设定。

**整型：**

- long long是C++11中新定义的

**浮点：**

- 可表示为单精度、双精度和扩展精度值

**带符号类型和无符号类型：**

> 除去布尔型和扩展的字符型之外，其它整型可以划分为**带符号的**和**无符号**两种

- 带符号类型：可以表示**正数**、**负数**、**0**
- 无符号类型：仅能表示**大于等于0**的值
- 通常在类型名前添加unsigned，就可以得到无符号类型
- 字符被分为了三种：char、signed char和unsigned char
- 类型char会根据编译器来决定用char还是signed char
- 8bit的signed char 计算机常常表示范围定为-128至127

**类型选择时注意事项：**

> - 明确知晓数值不可能为负时，选用无符号类型。
>
> - 整数运算用 int，数值太大时用 long long，不用 short 和 long
>
> - 浮点数运算用 double。float 和 double 的计算代价相差无几。

下面实例可以输出电脑上各种数据类型的大小：

```cpp
#include<iostream>  
#include <limits>
 
using namespace std;  
  
int main()  
{  
    cout << "type: \t\t" << "************size**************"<< endl;  
    cout << "bool: \t\t" << "所占字节数：" << sizeof(bool);  
    cout << "\t最大值：" << (numeric_limits<bool>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<bool>::min)() << endl;  
    cout << "char: \t\t" << "所占字节数：" << sizeof(char);  
    cout << "\t最大值：" << (numeric_limits<char>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<char>::min)() << endl;  
    cout << "signed char: \t" << "所占字节数：" << sizeof(signed char);  
    cout << "\t最大值：" << (numeric_limits<signed char>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<signed char>::min)() << endl;  
    cout << "unsigned char: \t" << "所占字节数：" << sizeof(unsigned char);  
    cout << "\t最大值：" << (numeric_limits<unsigned char>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<unsigned char>::min)() << endl;  
    cout << "wchar_t: \t" << "所占字节数：" << sizeof(wchar_t);  
    cout << "\t最大值：" << (numeric_limits<wchar_t>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<wchar_t>::min)() << endl;  
    cout << "short: \t\t" << "所占字节数：" << sizeof(short);  
    cout << "\t最大值：" << (numeric_limits<short>::max)();  
    cout << "\t\t最小值：" << (numeric_limits<short>::min)() << endl;  
    cout << "int: \t\t" << "所占字节数：" << sizeof(int);  
    cout << "\t最大值：" << (numeric_limits<int>::max)();  
    cout << "\t最小值：" << (numeric_limits<int>::min)() << endl;  
    cout << "unsigned: \t" << "所占字节数：" << sizeof(unsigned);  
    cout << "\t最大值：" << (numeric_limits<unsigned>::max)();  
    cout << "\t最小值：" << (numeric_limits<unsigned>::min)() << endl;  
    cout << "long: \t\t" << "所占字节数：" << sizeof(long);  
    cout << "\t最大值：" << (numeric_limits<long>::max)();  
    cout << "\t最小值：" << (numeric_limits<long>::min)() << endl;  
    cout << "unsigned long: \t" << "所占字节数：" << sizeof(unsigned long);  
    cout << "\t最大值：" << (numeric_limits<unsigned long>::max)();  
    cout << "\t最小值：" << (numeric_limits<unsigned long>::min)() << endl;  
    cout << "double: \t" << "所占字节数：" << sizeof(double);  
    cout << "\t最大值：" << (numeric_limits<double>::max)();  
    cout << "\t最小值：" << (numeric_limits<double>::min)() << endl;  
    cout << "long double: \t" << "所占字节数：" << sizeof(long double);  
    cout << "\t最大值：" << (numeric_limits<long double>::max)();  
    cout << "\t最小值：" << (numeric_limits<long double>::min)() << endl;  
    cout << "float: \t\t" << "所占字节数：" << sizeof(float);  
    cout << "\t最大值：" << (numeric_limits<float>::max)();  
    cout << "\t最小值：" << (numeric_limits<float>::min)() << endl;  
    cout << "size_t: \t" << "所占字节数：" << sizeof(size_t);  
    cout << "\t最大值：" << (numeric_limits<size_t>::max)();  
    cout << "\t最小值：" << (numeric_limits<size_t>::min)() << endl;  
    cout << "string: \t" << "所占字节数：" << sizeof(string) << endl;  
    // << "\t最大值：" << (numeric_limits<string>::max)() << "\t最小值：" << (numeric_limits<string>::min)() << endl;  
    cout << "type: \t\t" << "************size**************"<< endl;  
    return 0;  
}
```

结果如下：

```
type:           ************size**************
bool:           所占字节数：1   最大值：1               最小值：0
char:           所占字节数：1   最大值：                最小值：�
signed char:    所占字节数：1   最大值：                最小值：�
unsigned char:  所占字节数：1   最大值：�               最小值：
wchar_t:        所占字节数：2   最大值：65535           最小值：0
short:          所占字节数：2   最大值：32767           最小值：-32768
int:            所占字节数：4   最大值：2147483647      最小值：-2147483648
unsigned:       所占字节数：4   最大值：4294967295      最小值：0
long:           所占字节数：4   最大值：2147483647      最小值：-2147483648
unsigned long:  所占字节数：4   最大值：4294967295      最小值：0
double:         所占字节数：8   最大值：1.79769e+308    最小值：2.22507e-308
long double:    所占字节数：16  最大值：1.18973e+4932   最小值：3.3621e-4932
float:          所占字节数：4   最大值：3.40282e+38     最小值：1.17549e-38
size_t:         所占字节数：8   最大值：18446744073709551615    最小值：0
string:         所占字节数：32
type:           ************size**************
```

**练习** **2.1** **：**类型 int、long、long long 和 short 的区别是什么？无符号类型和带符号类型的区别是什么？float 和 double 的区别是什么？

**解答：**

1. 都属于整型，但是尺寸的最小值不同：short< int < long < long long 

   ```shell
   short int   2个字节      短整型
   int 		2/4字节      整型
   long 		4/8字节      长整型
   long long 	8字节        长整型 
   ```

    2.  带符号类型表示正数、负数（包括0），而无符号类型只能表示大于或等于0.如 int类型是无符号，需写成unsigend int ，表示大于或等于0的int整数。
       3.  float 和 double 分别是单精度浮点数和双精度浮点数，区别主要是在内存中所占的比特数不同，以及默认规定的有效位数不同。

**练习** **2.2** **：**计算按揭贷款时，对于利率、本金和付款分别应选择何种数据类型？说明你的理由。

**解答：**

   在实际应用中，利率、本金和付款既有可能是整数，也有可能是普通的实数。因此应该选择浮点类型来表 示。

   在可供选择的浮点类型： **float、double和 long double** ：

- double 和 float 的计算代价比较接近且表示范围更广，
- long double 的计算代价则相对较大，一般情况下没有选择的必要。
- 综合以上分析，选择 double  比较恰当的，利率如考虑丢失数据问题也可以考虑 float。

### **2.1.2 类型转换**

>  **不要混用符号类型和无符号类型。**
>
> 转换：将对象从一种给定的类型对象**转换**为另一种相关类型

 **几种类型转换的情况：**

1. 把浮点数赋给整型时，结果**仅保留小数点前的部分**。
2. 赋给无符号类型超出范围的值时，结果是**初始值对无符号类型表示数值总数取模后的余数**。比如 -1 赋给 8 位 unsigned char 的结果是 255（-1=256*(-1)+255）
3. **赋给带符号类型超出范围的值时，结果是未定义的**。程序可能工作，可能崩溃。



**含有无符号类型的表达式**

一个表达式中既有无符号数又有int值时，**int会被转换成无符号数**。

实例 

```cpp
#include <iostream>
int main()
{
   unsigned u = 10;
   unsigned j = 0;
   int i = -42;
   std::cout << i+i << std::endl; //输出 -42 
   std::cout << i+j << std::endl; //输出异常答案：4294967254 (2^32-42)
   std::cout << i+u << std::endl; //输出异常答案：4294967264 (2^32-32)

   int a = ~0;//按位取反运算，结果为(11111111111111111111111111111111)

   if( a>65536 )
   {
      std::cout<<"当前机器：32 bit:"<< a <<std::endl;
   }
   else
   {
      std::cout<<"当前机器：16 bit:"<< a <<std::endl;
   }
}
```

**无符号减无符号数，结果还是无符号数，如果是负值就等于该符数加上无符号数的模**



无符号整数减去一个值,不管这个值是不是无符号数，都确保不是负值

```cpp
#include <iostream>
int main()
{
   unsigned u = 42;
   unsigned j = 10;
   std::cout << u-j << std::endl; //输出 32 
   std::cout << j-u << std::endl; //输出为取模后的答案：4294967264(2^32-32)
}
```

如下代码 因为unsigned u永远不会小于0，会形成死循环

```cpp
for (unsigned u = 10; u >= 0; --u) {
        cout << u << endl;
}
```

 使用while循环来代替，u为0的时候可以跳出来

```cpp
unsigned u = 11;
    while (u > 0) {
        --u;
        cout << u << endl;
    }
```

> 切勿混用带符号类型和无符号类型

**练习** **2.3** **：**读程序写结果。

```cpp
#include <iostream>
int main()
{
   unsigned u=10, u2=42; 
   std::cout << u2-u << std::endl;  //32
   std::cout << u-u2 << std::endl;  //4294967264

   int i=10, i2=42; 
   std::cout << i2-i << std::endl;  //32
   std::cout << i-i2 << std::endl;  //-32
   std::cout << i-u << std::endl;   //0
   std::cout << u-i << std::endl;    //0
}
```

**练习** **2.4** **：**编写程序检查你的估计是否正确，如果不正确，请仔细研读本节直到弄明白问题所在。

**解答：**

通过 练习 2.3 为了理解无符号类型和带符号类型的区别，运行后，除了  u -u2,其他几项都比较好理解。着重理解 u-u2的问题。

分析：u -u2 计算时会把int值转换为无符号数，int是32位(4字节) **⭐4294967264怎么算呢？**

- -42的二进制表示(32位) 1111 1111 1111 1111 1111 1111 1101 0110 转换为无符号数计算为4294967295(2^32-1) - 1 - 8 - 32 = 4294967254

- 4294967254 + 10 = 4294967264

  

### **2.1.3 字面值常量**

> 字面值常量的形式和值决定了它的数据类型。如：42的值 为十进制字面值常量

#### **整型和浮点型字面值**

-  0 开头的整数是 8 进制, 如：024。
- 0x 开头的整数是十六进制，如：0x24。

- 十进制字面值是带符号数，类型是 int, long, long long 中能容纳当前值的尺寸最小的那个。

浮点型字面值可以用小数或科学计数法表示，科学计数法中的指数部分用 E 或 e 标识。 

```
3.14   0.  0e0  .001  3.14E2
```

#### **字符和字符串字面值**

**单引号**括起来的一个字符是 char 型字面值，**双引号**括起来的 0 个或多个字符则构成**字符串型字面值**。

```
'a' 				// 字符字面值
"hello world!"		// 字符串字面值
```

字符串字面值的类型实际上是常量字符构成的**数组（Array）**. 编译器会向每个字符串结尾添加一个空字符**（'\0'）**

因此字符串字面值的实际长度要比它的内容多 1, 如 “A” 代表了一个长度为 2 的字符数组。

```cpp
#include <iostream>
#include <cstring>   //string.h的C++版本
using namespace std;
int main() {
    char a = 'a';
    char cal[] = "HelloWorld";
    cout << sizeof(a) << endl;    //1
    cout << sizeof(cal) << endl;  //11,包括了空字符
    cout << strlen(cal) << endl;  //10,空字符不计算在内
    return 0; 
}
```

如果两个字符串字面值紧邻且仅由空格、缩进和换行符分隔，则它们实际上是一个整体。因此字符串比较长时可以直接分行书写。

​                "A is B"   "and B is A"; //两个字符串实际上是一个整体。          

```cpp
#include <iostream>
#include <cstring>   //string.h的C++版本
using namespace std;
int main() {
    char a = 'a';
    char cal[] =  "A is B"   "and B is A";
    cout << sizeof(a) << endl;    //1
    cout << sizeof(cal) << endl;  //11,包括了空字符
    cout << strlen(cal) << endl;  //10,空字符不计算在内
    cout << "yeah a really"
        "really long string literal" << endl;  // 允许多行书写字符串字面量  
    return 0; 
}
```

  

#### **转义序列**

有俩类字符程序员不能直接使用的字符：

1. 不可打印的字符，如退格或其他控制字符等 
2. 有特殊含义的字符（单引号、双引号、问号、反斜线）

这时候需要转义序列（escape sequence）, 转义序列均以**反斜线**作为开始。

![image-20230924110241635](.\img\image-20230924110228231.png)

```cpp
#include <iostream>
using namespace std;
int main() {
    char cal[] =  "A is B and B is A\n";
    cout << cal << endl;  
     cout << "\t" << cal << endl;  
    cout << "yeah a really \n"
        "really long string literal" << endl; 
    return 0; 
}
```

运行后结果：

```cpp
A is B and B is A

        A is B and B is A

yeah a really
really long string literal
```

也可以使用 泛化的转义序列，在\x后紧跟1个或多个十六进制数字，或者\后紧跟1个、2个或3个八进制数字。

![image-20230924111157249](.\img\image-20230924111157249.png)

```cpp
#include <iostream>
using namespace std;
int main() {
    cout << "Hi \x4dO\115!\n\1234\x1234" << endl;  //输出 Hi MOM! ，转到新一行 , S44 
    return 0; 
}
```

**注意：**

如："\1234"后面表示2个字符，即八进制数123对应的字符以及字符4

如："\x1234"表示一个16位的字符

#### **指定字面值的类型**

通过前缀和后缀，可以改变整型、浮点型和字符型字面值的默认类型。

![image-20230924112151683](.\img\image-20230924112151683.png)

**布尔字面值和指针字面值**

true 和  false // bool 类型的字面值 

nullptr    // 指针字面值   

**练习** **2.5** **：**指出下述字面值的数据类型并说明每一组内几种字面值的区别：

(a) 'a', L'a', "a", L"a" 

(b) 10, 10u, 10L, 10uL, 012, 0xC 

(c) 3.14, 3.14f, 3.14L 

(d) 10, 10u, 10., 10e-2 

**解答：**

```shell
(a):
1. 'a'		字符 a，    
2. L'a'		宽字符型字面值 a且类型是 wchar_t，
3. ＂a＂	   字符串 a，
4. L＂a＂	   宽字符型字符串 a
(b):
1. 10 		整数类型字面值
2. 10u 		无符号数
3. 10L 		长整型数
4. 10uL     无符号长整型数
5. 012      八进制数（对应十进制10）
6. 0xC      十六进制数（对应十进制12）
(c):
1. 3.14 		一个普通的浮点类型字面值
2. 3.14f 		一个 float 类型的单精度浮点数
3. 3.14L 		一个 long double 类型的扩展精度浮点数
(d):
1. 10 			一个整数
2. 10u 		    一个无符号整数
3. 10.			一个浮点数
4. 10e-2 		一个科学计数法表示的浮点数，大小为 10*10-2=0.1
```

 **练习** **2.6** **：**下面两组定义是否有区别，如果有，请叙述之：

int month = 9, day = 7; 

int month = 09, day = 07;       

**出题思路：**

考察十进制数字与八进制数字的表示方法。

**解答：**

 第一组定义是正确的，定义了两个十进制数 9 和 7。

第二组定义是错误的，编译时将报错。因为以 0 开头的数是八进制数，而数字 9显然超出了八进制数能表示的范围，所以第二组定义无法被编译通过。



**练习** **2.7** **：**下述字面值表示何种含义？它们各自的数据类型是什么？

(a) "Who goes with F\145rgus?\012" 

(b) 3.14e1L 

(c) 1024f

 (d) 3.14L 

**解答：**

```shell
(a) 字符串，包含两个转义字符 \145表示字符e,\012表示一个换行符，结果：Who goes with Fergus? 加航换行
(b) 科学计数法表示的扩展精度浮点数，大小为3.14*10^1 = 31.4 
(c) 转单精度浮点数，但是形式错误，某些编译器将报错，需改为：1024.f
(d) 扩展精度浮点数，类型 long double, 大小为3.14 
```

**练习** **2.8** **：**请利用转义字符编写一段程序，要求先输出 2M，然后转到新一行。修改程序使其先输出 2，然后输出制表符，再输出 M，最后转到新一行。

**解答：**

```cpp
#include <iostream>
using namespace std;
int main() {
    cout << "2\115\n" << endl; 
    cout << "2\t\115\n" << endl; 
    return 0; 
}
```



## **2.2 变量**

> 变量提供一个具名的、可供程序操作的存储空间。

对于c++而言，”变量“和”对象“一般可以互换使用。

### **2.2.1 变量定义**

#### **初始化**

**对象在创建时获得一个特定的值**

```
int sum = 0,value , units_sold = 0;
Sales_item item;  // （见1.5.1节实例）
```

可以在同一条定义语句中使用先定义的变量去初始化后定义的其他变量。

```
       double price = 109.99, discount = price * 0.6;            
```

  **初始化和赋值的区别：**

初始化不是赋值，初始化是创建变量时赋予一个初始值

赋值是把对象的当前值**擦除**并用一个新值来替代。

#### **列表初始化**

下面四种初始化方式都是可行的，其中**使用花括号的方式叫做列表初始化**。

```cpp
            int i=0;  int i={0};  int i{0};  int i(0);         
```

使用列表初始化且初始值存在信息丢失的风险，**编译器会报错**。

```cpp
long double ld = 3.1415926536; 
int a{ld}, b={ld};  //错误，存在信息丢失的风险，转换未执行。 
int c(ld), d=ld;    //正确      
```

#### **默认初始化**

> 如果定义变量时没有指定初值，则变量被默认初始化

定义于函数体内的内置类型的对象.如果没有初始化，则其值**未定义**。定义于任何函数之外的内置类型则被初始化为0；

类的对象如果没有显式地初始化，则其由类确定。string 默认初始化为一个空串。

不能使用未初始化的变量，否则会引发运行时故障。

```cpp
#include <iostream>
using namespace std;
int m;
int main() {
    int a;
    cout << m << endl;  //0
    cout << a << endl;  //wrong：使用了未初始化的局部变量a (可能改进了)
    return 0; 
}
```

**建议初始化每一个内置类型的变量,虽然并非必须这么做，但如果我们不能确保初始化后程序安全，那么这么做不失为一种简单可靠的方法。**

**练习** **2.9** **：**解释下列定义的含义。对于非法的定义，请说明错在何处并将其改正。

(a) std::cin >> int input_value; (b) int i = { 3.14 }; 

(c) double salary = wage = 9999.99; (d) int i = 3.14; 

**解答：**

```shell
(a): 报错 ，输入运算符的右侧需要是一个明确的变量名称
     int input_value; 
     std::cin >> input_value; 
(b): 引发警告，通过列表初始化的方式改3.14赋值给i,造成小数位部分丢失。
(c): 错误，声明语句有多个变量时要用逗号将变量名隔开，应改为：
      double salary ,wage;
      salary = wage = 9999.99;
      
(d): 引发警告，跟（b）一样是不被建议的窄化操作。

```

**练习** **2.10** **：**下列变量的初值分别是什么？

```cpp
#include <iostream>
using namespace std;
std::string global_str; 

int global_int; 

int main() 
{ 
   int local_int; 
   std::string local_str;

   cout << global_str << endl;  //空
   cout << global_int << endl;  //0
   cout << local_int << endl;   //0
   cout << local_str << endl;   //空
} 
```

### **2.2.2 变量声明和定义的关系**

> C++语言支持分离式编译(seperate complication)机制

**声明**和**定义**是严格区分的。

- 要声明一个变量加 extern，声明变量不能赋值。

- 任何包含了显式初始化的声明即成为定义。
- 变量只能被定义一次，但是可以多次声明。

```
extern int i;     // 声明 i 
int i;            // 定义i； 
extern int i = 1; // 定义 i，初始化抵消了 extern 的作用。
```

声明和定义的区分很重要。

**用法：**如果要在多个文件中使用同一个变量，就必须将声明和定义分离，变量定义必须且只能出现在一个文件里。

c++是**静态类型语言**，其含义是**在编译阶段检查类型**。

**练习** **2.11** **：**指出下面的语句是声明还是定义：

(a) extern int ix = 1024; 

(b) int iy; 

(c) extern int iz; 

**解答：**

```cpp
(a) extern int ix = 1024;  // 定义
(b) int iy;                // 定义
(c) extern int iz;         // 声明 
```

### **2.2.3 标识符**

>  **标识符组成：**
>
> 字母、数字、下划线。不能以数字开头，
>
> 对大小写敏感。标识符的长度没有限制。
>
> 用户自定义的标识符不能连续出现两个下划线，
>
> 也不能以下划线紧连大写字母开头。
>
> 定义在函数体外的标识符不能以下划线开头。

**变量命名规范：**

1. 标识符要体现其实际含义。
2. 变量名一般用小写字母。
3. 用户自定义的类型一般以大写字母开头。
4. 包含多个单词的标识符，使用驼峰命名法或使用下划线连接不同单词。

对于嵌套作用域，可以在内层作用域中重新定义外层作用域已有的名字，但是最好不要这样做。

> 对于命名规范来说，若能坚持，必将有效。

![image-20230924161850075](.\img\image-20230924161850075.png)

**练习** **2.12** **：**请指出下面的名字哪个是非法的？

(a) int double = 3.14; (b) int _; 

(c) int catch-22; (d) int 1_or_2 = 1; 

(e) double Double = 3.14; 

**解答**

```cpp
(a) int double = 3.14;    // 非法 ，关键字不允许
(b) int _;                // 合法，但是不能两个下划线
(c) int catch-22;         // - 符号不允许 可以是下划线，字母，数字
(d) int 1_or_2 = 1;       // 非法，不能以数字开头
(e) double Double = 3.14; // 合法 
```



### 2.2.4 名字的作用域

> **作用域**:是程序的一部分，大多数作用域都以花括号分隔。

⭐注意：名字的有效区始于名字的声明语句，以声明语句所在的作用域末端结束

- main拥有全局作用域，名字在整个程序范围内都可使用，main内定义的变量拥有块作用域

  ```cpp
  int reused = 42;  //全局作用域
  int main() {
      int unique = 0;  //块作用域
      cout << reused << endl;   //42
      int reused = 0; 
      cout << reused << endl;  //新建局部变量覆盖了全局变量
      cout << ::reused << endl; //显示访问全局变量，此时reused正在作用域内
      return 0;
  }
  ```

#### **嵌套的作用域**

> 被包含的作用域称为**内层作用域**，包含别的作用域的作用域称为**外层作用域**
> **注意：** ::reused //显示访问全局变量

**练习** **2.13** **：**下面程序中 j 的值是多少？

int i = 42; 

int main() 

{ 

int i = 100; 

int j = i; 

} 

**解答:**

```cpp
#include <iostream>
using namespace std;
int i = 42; 
int main() 
{ 
   int i = 100; 
   int j = i; 
   cout << j << endl;  //100
} 
```

**练习** **2.14** **：**下面的程序合法吗？如果合法，它将输出什么？

int i = 100, sum = 0; 

for (int i = 0; i != 10; ++i) 

sum += i; 

std::cout << i << " " << sum << std::endl; 

**解答：**  该程序是合法的，输出结果是 100 45 

```cpp
#include <iostream>
using namespace std;
int i = 42; 
int main() 
{ 
   int i = 100, sum = 0; 
   for (int i = 0; i != 10; ++i) 
      sum += i; 
   std::cout << i << " " << sum << std::endl;  // 100 45 
} 
```

## **2.3 复合类型**

复合类型：基于其他类型定义的类型，引用和指针是其中两种。

### **2.3.1 引用**

> 严格来说，使用术语"引用"时，指的是"左值引用"（lvalue reference）
>
> C++11 中新增了一种引用：“右值引用（rvalue reference）”,以后再介绍。

**定义：为对象起了另外一个名字**，引用类型引用另外一种类型，通过将声明符写成&d的形式来定义引用类型，其中d是声明的变量名：

```cpp
int ival = 1024;     
int &refVal = ival;    // refVal 指向ival (是ival的另一个而名字)
int &refVal2;          // 报错：引用必须被初始化 
```

⭐**引用必须被初始化**,**引用的初始值必须是一个对象，不能是字面值**

一般在初始化变量时，初始值会被拷贝到新建的对象中。然而在定义引用时，程序把引用和它的初始值**绑定**(bind)在一起，而不是将初始值拷贝给引用，一旦初始化完成，引用和它的初始值对象一直绑定在一起，因此无法令引用重新绑定到另一个对象，因此引用必须初始化。

#### 引用即别名

>  **引用非对象, 相反的，它只是为一个已经存在的对象所起的另外一个名字。**

```cpp
refVal = 2;    			// 将2赋给refVal指向的对象，此处即是赋给了ival.
int  ii = refVal        // 与 ii = ival 执行结果一样 
```

```
int &refVal3 = refVal; // 正确
int i = refVal         // 正确 i被初始化为ival的值

```

- 引用只能绑定在对象上，不能与字面值或表达式绑定。

- 引用只能绑定同类型对象。

通过完整的代码查看：

```cpp
#include <iostream>
using namespace std;
int main() {
    int ival = 1024;
    int &refVal = ival;
    cout  << " ival: " << ival << ", refVal :" << refVal << ", &refVal : "
          << &refVal << endl;
    refVal = 2;
    cout  << " ival: " << ival << ", refVal :" << refVal << ", &refVal : "
          << &refVal << endl;
    int ii = refVal;
    cout  << " ival: " << ival << ", ii :" << ii << endl;
    int &refVal3 = refVal;
     cout  << " refVal3: " << refVal3 << ",  &refVal3: " 
           << &refVal3 << ",refVal :" << refVal << ", &refVal : "
           << &refVal << endl;
    return 0;
}
```

结果如下：

```cpp
ival: 1024, refVal :1024, &refVal : 0x61fe04
 ival: 2, refVal :2, &refVal : 0x61fe04
 ival: 2, ii :2
 refVal3: 2,  &refVal3: 0x61fe04,refVal :2, &refVal : 0x61fe04
```

#### 引用的定义

```cpp
int i = 1024,i2 = 2048;   	// 都是int
int &r = i ,r2 = i2;		// r 引用与i绑定在一起，r2是int
int i3 = 1024,&ri = i3;     // r3 是 int ,ri 是引用，与r3绑定在一起
int &r3 = i3,&r4 = r2;      // r3 和 r4是引用
```

> ? 抛出问题：除了两种例外情况，其他所有引用的类型都要与之绑定的对象严格匹配。而且，引用只能绑定在对象上，而不能与字面值或某个表达式的计算结果绑定在一起。

```cpp
int &refVal4 = 10;  		// 错误：引用类型的初始值必须是一个对象
double dval = 3.14;			
int &refVal5 = dval;		// 错误：此处引用类型的初始值必须是 int 型对象 
```

引用通常用于函数参数列表和函数返回值。下面列出了 C++ 程序员必须清楚的两个与 C++ 引用相关的重要概念：

| 概念                                                         | 描述                                                     |
| :----------------------------------------------------------- | :------------------------------------------------------- |
| [把引用作为参数](https://www.runoob.com/cplusplus/passing-parameters-by-references.html) | C++ 支持把引用作为参数传给函数，这比传一般的参数更安全。 |
| [把引用作为返回值](https://www.runoob.com/cplusplus/returning-values-by-reference.html) | 可以从 C++ 函数中返回引用，就像返回其他数据类型一样。    |

**练习** **2.15** **：**下面的哪个定义是不合法的？为什么？

(a) int ival = 1.01; 

(b) int &rval1 = 1.01; 

(c) int &rval2 = ival; (d) int &rval3; 

**解答：**

```cpp
(a) int ival = 1.01;   		// 合法，不过数据丢失小数位
(b) int &rval1 = 1.01;      // 非法：指向对象而非字面值常量
(c) int &rval2 = ival; 		// 合法
(d) int &rval3; 			// 非法，引用必须初始化
```

**练习** **2.16** **：**考查下面的所有赋值然后回答：哪些赋值是不合法的？为什么？哪些赋值是合法的？它们执行了什么样的操作？

int i = 0, &r1 = i; double d = 0, &r2 = d; 

(a) r2 = 3.14159; (b) r2 = r1; 

(c) i = r2; (d) r1 = d; 

**解答：**

```cpp
int i = 0, &r1 = i; double d = 0, &r2 = d; 

(a) r2 = 3.14159;  // 合法，结果d = 3.14159 
(b) r2 = r1;       // 合法  d = i 
(c) i = r2;        // 合法  i = d ,并且执行了窄化操作
(d) r1 = d;        // 合法  i = d ,同样执行了窄化操作 
```

**练习** **2.17** **：**执行下面的代码段将输出什么结果？

int i, &ri = i; 

i = 5; ri = 10; 

std::cout << i << " " << ri << std::endl; 

**解答：**

```cpp
#include <iostream>
using namespace std;
int main() 
{ 
   int i, &ri = i; 
   i = 5; ri = 10; 
   std::cout << i << " " << ri << std::endl;   // 结果：10 10 
} 
```



### **2.3.2 指针**

- 指针是一个对象，允许对指针赋值和拷贝。

- 指针无须在定义时赋初值，如果块作用域内定义的指针没有被初始化，也将拥有一个不确定的值。
- 指针是指向另一种类型的复合类型，允许对其它对象的间接访问
- 指向某块内存的地址

定义指针的方法将声明符写成$*d$的形式，其中$d$是变量名。

```cpp
int *ip1,*ip2;  		// ip1 和ip2都是指向int型对象的指针
double dp, *dp2;		// dp2 是指向double型对象的指针，dp是double型对象 
int ival = 42;
int* ip1 = &ival;		// ip1存放变量ival的地址，把ip1定义为指向int的指针
```

```cpp
#include <iostream>
using namespace std;
int main() 
{ 
    int ival = 42;
    int* p = &ival;  
    int* p2= p;
    cout << *p << endl;      //42
    cout << p << endl;       //ival的内存地址 （0x61fe14）
    cout << p2 << endl;      //ival的内存地址 （0x61fe14）
    return 0;
} 
```

**指针必须指向指定的类型，不能指向其他类型**。

```cpp
int i = 0; double *dp = &i;   	// 错误 
long *lp = &i;     				// 错误 
int *ip = i;       				// 这个也是错误的，但 int *ip = 0; 是正确的 
```

**不能定义指向引用的指针。可以定义指向指针的引用。**

```cpp
int *p;  int* &r = p;      // r是对指针p的引用          
```

面对如上 *&r 这样比较复杂的指针或引用的声明语句时，从右向左读比较易于弄清。

利用解引用符（*）可以访问指针指向的对象。

```cpp
#include <iostream>
using namespace std;
int main() 
{ 
    int i = 42;
    int &r = i;				// &紧随类型名出现，因此是声明的一部分，r是一个引用
    int *p;					// *紧随类型名出现，因此是声明的一部分，p是一个指针
    p  = &i;				// &出现在表达式中，是一个取地址符
    *p = i;                 // *出现在表达式中，是一个解引用符
    int &r2 = *p;           // & 是声明的一部分，*是一个解引用符 
    cout << p << endl;      //ival的内存地址 （0x61fe14）
    cout << *p << endl;     //42
    cout << &r2 << endl;     //ival的内存地址 （0x61fe14）
    return 0;
}   
```

在声明语句中，& 和 * 用于组成复合类型，在表达式中，它们的角色又转变成运算符。

#### **空指针**

不指向任何对象，

```cpp
int *p = nullptr; // 三种定义空指针的方式。最好用第一种  等价于 int *p1 = 0;
int *p = 0;       // 直接将p初始化为字面常量0
// 需要首先 #include cstdlib 
int *p = NULL;    // 预处理变量 NULL 等于 int *p = 0;  
```

关于**预处理器**

- 运行于编译过程之前的一段程序
- 预处理变量，不属于命名空间std，由预处理器负责管理,因此预处理变量前面无须加上std::。

```cpp
#include <iostream>
using namespace std;
int main() 
{ 
    int* p1 = nullpt;  
    int zero = 0;
   // p1 = zero;  //错误，不能把int变量直接赋给指针
   *p1 = zero; //正确
    cout << *p1 << endl;       //解引用 0
    return 0;
}   
```

>  **tips:建议初始化所有指针。**

#### 赋值和指针

给指针赋值就是令它存放一个新的地址，从而指向一个新的对象；

```cpp
int val = 0;
int* p = nullptr;
p = &val;
```

赋值永远改变的是等号左侧的对象。

```
p = &val;   // p 的值被改变，现在p指向了val
```

意思是p 赋了一个新的值，也就是改变了哪个存放在p内的地址值。相反的，如果写成:

```
*p = 0;      // val的值被改变，指针p并没有变
```

*p(也就是指针p指向的哪个对象)发生改变 。

两个类型相同的合法指针，可以用相等操作符（==）或不相等操作符（!=）来比较它们，比较结果是布尔类型。



#### **void\*指针**

void* 指针和空指针不是一回事。

void* 指针是特殊的指针类型，可以存放任意对象的地址。它的用处比较有限。

**void\*能做的事**：

- 拿它和别的指针比较
- 作为函数的输入或输出
- 赋给另外一个void*指针

⭐不能直接操作void*指针所指的对象

```cpp
double obj = 3.14, * pd = &obj;
    void* pv = &obj; //obj可以是任意类型对象
    pv = pd;   //可以存放任意类型的指针
```

#### 指针与引用的区别（不充分）

- 不存在空引用。引用必须连接到一块合法的内存。
- 一旦引用被初始化为一个对象，就不能被指向到另一个对象。指针可以在任何时候指向到另一个对象。
- 引用必须在创建时被初始化。指针可以在任何时间被初始化。

- 指针本身就是一个对象，需要分配内存。引用是别名，不需要分配内存。

- 引用的创建和销毁不会调用类的拷贝构造函数和析构函数。

- 不存在引用的引用，也不存在引用的指针

- 指针需要解引用，引用无需解引用

- 指针可以有多级，但是引用只能是一级（int **p；合法 而 int &&a是不合法的）；

- 指针的++，--代表下一个数据，**引用的++，--代表数据本身的加减**。

  

**练习** **2.18** **：**编写代码分别更改指针的值以及指针所指对象的值。

**解答：**

```cpp
#include <iostream>
using namespace std;
int main() 
{ 
   int i = 5,j = 10;
   int *p = &i;
   cout<< "p = " << p << ", *p = " << *p << endl; // 答案：p = 0x61fe14, *p = 5
   p = &j;
   cout<< "p = " << p << ", *p = " << *p << endl; // 答案：p = 0x61fe10, *p = 10
   *p = 20;
   cout<< "p = " << p << ", *p = " << *p << endl; // 答案：p = 0x61fe10, *p = 20
   j = 30;
   cout<< "p = " << p << ", *p = " << *p << endl; // 答案：p = 0x61fe10, *p = 30
   return 0 ;
}   
```

**练习** **2.19** **：**说明指针和引用的主要区别。

**解答**

**相同:**

指针和引用都是复合类型，都与内存中实际存在的对象有联系。

**区别：**

1. 指针本身就是一个对象，允许对指针赋值和拷贝，引用不是一个对象。

2. 指针的声明周期内可以指向几个不同的对象，引用无法重新绑定到另一个对象。

3. 指针无须在定义时赋初值，引用则必须在定义时赋初值。

4. 有指向指针的指针，无引用的引用。

   

**练习** **2.20** **：**请叙述下面这段代码的作用。

int i = 42; 

int *p1 = &i; 

*p1 = *p1 * *p1; 

**解答**

```cpp
#include <iostream>
using namespace std;
int main() 
{ 
   int i = 42; 
   int *p1 = &i; // 声明一个指针
   cout<< "p1 = " << p1 << ", *p = " << *p1 << endl; // 答案：p1 = 0x61fe14, *p = 42
   *p1 = *p1 * *p1; //解引用运算，即取出指针p1所指的对象的值 
   cout<< "p1 = " << p1 << ", *p = " << *p1 << endl; // 答案：p1 = 0x61fe14, *p = 1764
   return 0 ;
}   
```

**练习** **2.21** **：**请解释下述定义。在这些定义中有非法的吗？如果有，为什么？

int i = 0; 

(a) double* dp = &i; (b) int *ip = i; (c) int *p = &i; 

**解答**

```cpp
(a) double* dp = &i;  // 非法 dp是double指针，i是int变量，类型不匹配
(b) int *ip = i;      // 非法，指针不允许直接int变量赋值，需要取地址运算符 &i 
(c) int *p = &i;      // 合法 
```

**练习** **2.22****：**假设 p 是一个 int 型指针，请说明下述代码的含义。

if (p) // ... 

if (*p) // ... 

**解答：**

```cpp
#include <iostream>
int main ()
{
    int i = 0;
    int *p1 = nullptr;
    int *p = &i;
    if (p1) // 检验指针的值（即指针所指对象的地址）
        std::cout << "p1 pass" << std::endl;
    if (p) // 检验指针的值（即指针所指对象的地址）
        std::cout << "p pass" << std::endl;
    if (*p) // 检验指针所指对象的值
        std::cout << "i pass" << std::endl;
    return 0;
}
```

**练习** **2.23** **：**给定指针 p，你能知道它是否指向了一个合法的对象吗？如果能，叙述判断的思路；如果不能，说明原因。

**解答**

```cpp
在 C++程序中，应该尽量初始化所有指针，并且尽可能等定义了对象之后再定义指向它的指针。如果实在不清楚指针应该指向何处，就把它初始化为 nullptr 或者 0，这样程序就能检测并知道它有没有指向一个具体的对象了。其中，nullptr是 C++11 新标准刚刚引入的一个特殊字面值，它可以转换成任意其他的指针类型。
在此前提下，判断 p 是否指向合法的对象，只需把 p 作为 if 语句的条件即可，如果p 的值是 nullptr，则条件为假；反之，条件为真。如果不注意初始化所有指针而贸然判断指针的值，则有可能引发不可预知的结果。一种处理的办法是把 if(p)置于 try 结构中，当程序块顺利执行时，表示 p 指向了合法的对象；当程序块出错跳转到 catch 语句时，表示 p 没有指向合法的对象。
```

**练习** **2.24****：**在下面这段代码中为什么 p 合法而 lp 非法？

int i = 42; void *p = &i; long *lp = &i; 

**解答**

```cpp
p是合法的，void 是一种特殊的指针类型，可用于存放任意对象的地址。
lp是非法的，long 和 int 两者的类型不匹配
```



### **2.3.3 理解复合类型的声明**

```cpp
int* p1,p2; //p1是指向int的指针，p2是int变量
int *p1, *p2; //都是指向int的指针
```

####    指向指针的指针

```cpp
int ival = 1024;
int* pi = &ival;  //pi 指向一个int型的数
int** ppi = &pi;  //ppi 指向一个int型的数
```

![image-20230925155519629](.\img\image-20230925155519629.png)

```cpp
#include <iostream>
int main ()
{
    int ival = 1024;
    int* pi = &ival;  //pi 指向一个int型的数
    int** ppi = &pi;  //ppi 指向一个int型的数
    std::cout << "the value of ival \n"
         << "direct value: " << ival << "\n"
         << "indirect value: " << *pi << "\n"
         << "doubly indirect value: " << **ppi << ", ppi = " << ppi << " , *ppi = " << *ppi 
         << std::endl; 
}
```

运行得到结果：

```cpp
the value of ival 
direct value: 1024
indirect value: 1024
doubly indirect value: 1024, ppi = 0x61fe08 , *ppi = 0x61fe14
```

#### **指向指针的引用**

从右往左读r第一个是&，所以r是一个引用

```cpp
int i = 42;
int *p;            // p 是一个int型指针
int *&r = p;       // r是一个对指针p的引用
r = &i;            // r引用了一个指针，因此给r赋值&i就是令p指向i
*r = 0;            // 解引用r得到i,也就是p指向的对象，将i的值改为0 
```

**练习** **2.25** **：**说明下列变量的类型和值。

(a) int* ip, i, &r = i; (b) int i, *ip = 0; (c) int* ip, ip2; 

**解答：**

```cpp
(a) int* ip, i, &r = i;    // ip是整型指针， i是整型数，r 是一个引用,r的值就是i的值
(b) int i, *ip = 0;        // i是整形数，ip是整型指针，它不指向任何具体的对象，初始化为0
(c) int* ip, ip2;          // ip是整型指针，ip2是整型数 
```

## **2.4 const限定符**

定义一种变量，希望它的值不能被改变，const对象一旦创建后，值就不能再改变，

⭐**const对象必须初始化，**因为一旦创建就不能再改变值

⭐**const int n 和 int const n等价**

> 1. 默认情况下，const 对象仅在文件内有效。 
>
> 2. 如果想在多个文件间共享 const 对象，必须在变量的定义前添加 extern 关键字并在本文件中声明。
>
> 3. 声明和定义都要加 extern

**练习** **2.26** **：**下面哪些句子是合法的？如果有不合法的句子，请说明为什么？

(a) const int buf; 

(b) int cnt = 0; 

(c) const int sz = cnt; 

(d) ++cnt; ++sz; 

**解答**

```cpp
(a) const int buf;      // 非法，未初始化 
(b) int cnt = 0;   		// 合法
(c) const int sz = cnt; // 合法
(d) ++cnt; ++sz;        // 非法，sz是const对象，其指不能被改变 
```

### **2.4.1 const的引用**

可以把引用绑定到 const 对象上,就像绑定到其他对象上一样,我们称之为**对常量的引用**.

- 引用必须初始化，因此常量引用也必须初始化。

- 不能用非常量引用指向一个常量对象。可以用常量引用指向一个非常量对象。
- 注意引用不是对象，因此常量引用不是说引用是常量，引用本来就只能绑定一个对象，而是引用不能改变引用的对象了。

```cpp
const int ci = 1024;
const int &ri = ci;   // 正确：引用对应的对象都是常量，类似临时量对象 
r1 = 42;              // 错误：r1 是对常量的引用
int &r2 = ci;         // 错误：试图让一个非常量引用指向一个常量对象 
```

引用的类型必须与其所引用对象的类型一致，但是有两个例外。

- 其中一个例外就是初始化常量引用时允许用任意表达式作为初始值（包括常量表达式），只要该表达式结果可以转换为引用的类型。

```
const int &r = 42;  // 常量引用可以绑定字面值       
```

当用常量引用绑定一个非常量对象时，不能通过引用改变引用对象的值，但是可以通过其他方式改变值。常量指针也一样。

常量引用仅对可参与的操作做出了限定，**对于引用的对象本身是不是一个常量并未做限定。**

```cpp
#include <iostream>
int main ()
{
    int i = 5;
    const int& a = i;
    i = 0;  //不可以通过a修改i的值，但是i本身可以赋值
    std::cout << a << " " << i << std::endl; // 运行通过：0  0 
}
```

对常量的引用不能被用作修改它所绑定的对象

```cpp
const int ci = 1024;
const int& ri = ci;
ri = 42; //错误，ri是对常量的引用
int& r2 = ci; //错误，试图让一个非常量引用指向一个非常量对象
```



### **2.4.2 指针和const**

- 指向常量的指针(pointer to const)不能用于改变所指对象的值，要想存放常量对象的地址，只能使用指向常量的指针
- 允许常量指针指向一个非常量对象(这是指针类型必须与其所指对象类型一致的例外之一),和常量引用一样，指向常量的指针也没有规定其所指的对象必须是一个常量，仅仅要求不能通过该指针改变对象的值。

```cpp
const double pi = 3.14;
double *cpt = &pi        // 错误：cpt是一个普通指针
const double* ptr = &pi; // 正确：要想存放常量对象的地址，只能使用指向常量的指针
*ptr =  42;              // 错误：不能给*ptr赋值，来改变pi的值 
```

**const指针**，**指针本身为常量，常量指针必须初始化**

```cpp
int errNumb = 0;
int* const curr = &errNumb;  //curru将一直指向errNumb
```

**练习** **2.27** **：**下面的哪些初始化是合法的？请说明原因。

(a) int i = -1, &r = 0; (b) int *const p2 = &i2; 

(c) const int i = -1, &r = 0;(d) const int *const p3 = &i2; 

(e) const int *p1 = &i2; (f) const int &const r2; 

(g) const int i2 = i, &r = i; 

**解答：**

```cpp
(a) int i = -1, &r = 0;        // 非法 ，非常量引用r不能引用字面值常量0 
(b) int *const p2 = &i2;       // 合法， p2是常量指针，p2的值永不改变，即p2永远指向i2
(c) const int i = -1, &r = 0;  // 合法   i 是常量 ，r是常量引用初始值为0 
(d) const int *const p3 = &i2; // 合法   P3是常量引用，p3永远指向i2 
(e) const int *p1 = &i2;       // 合法   p1指向一个常量，不能通过p1改变所指对象的值。
(f) const int &const r2;       // 非法 ，引用本身不是对象，因此不能让引用恒定不变
(g) const int i2 = i, &r = i;  // 合法 ，i2是常量，r也是常量引用
```

**练习** **2.28****：**说明下面的这些定义是什么意思，挑出其中不合法的。

(a) int i, *const cp; (b) int *p1, *const p2; 

(c) const int ic, &r = ic; (d) const int *const p3; 

(e) const int *p; 

**解答：**

```cpp
(a)是非法的，cp 是一个常量指针，因其值不能被改变，所以必须初始化。
(b)是非法的，cp2 是一个常量指针，因其值不能被改变，所以必须初始化。
(c)是非法的，ic 是一个常量，因其值不能被改变，所以必须初始化。
(d)是非法的，p3 是一个常量指针，因其值不能被改变，所以必须初始化；同时p3 指向的是常量，即我们不能通过 p3 改变所指对象的值。
(e)是合法的，但是 p 没有指向任何实际的对象。
```

**练习** **2.29****：**假设已有上一个练习中定义的那些变量，则下面的哪些语句是合法

的？请说明原因。

(a) i = ic; 

(b) p1 = p3; 

(c) p1 = ⁣ (d) p3 = ⁣ 

(e) p2 = p1; 

(f) ic = *p3; 

**解答：**

```cpp
(a)是合法的，常量 ic 的值赋给了非常量 i。
(b)是非法的，普通指针 p1 指向了一个常量，从语法上说，p1 的值可以随意改
变，显然是不合理的。
(c)是非法的，普通指针 p1 指向了一个常量，错误情况与上一条类似。
(d)是非法的，p3 是一个常量指针，不能被赋值。
(e)是非法的，p2 是一个常量指针，不能被赋值。
(f)是非法的，ic 是一个常量，不能被赋值。
```

### **2.4.3 顶层const**

**认识顶层const 和底层const**

- **顶层 const** 表示**指针本身**是个常量，**底层 const** 表示**指针所指的对象**是一个常量。

- 顶层 const 对任何数据类型通用，**底层 const** 只用于引用和指针。

- 顶层 const 的指针表示该指针是 const 对象，因此必须初始化。底层 const 的指针则不用。

```cpp
int i = 0;
int *const p1 = $i;		// 不能改变p1的值，这是一个顶层const
const int ci = 42; 		// 不能改变ci的值，这是一个顶层const
const int *p2 = &ci;    // 允许改变p2的值，这是一个底层const 
const int *const p3 = p2; // 靠右的const是顶层const,靠左的是底层const
const int &r = ci		// 用于声明引用的const 都是底层const 
```

如`const int &r = ci`,**拷贝时，拷入和拷出的对象必须是底层const**

实际上只有指针类型既可以是顶层 const 也可以是底层 const，因为引用实际上只能是底层 const，常量引用即为底层 const，不存在顶层 const 的引用。

```cpp
const int &const p2 = p1;// 错误  不能改变p1的值，这是一个顶层const 
```

从右向左读来判断是顶层 const 还是底层 const。

**对于指针和引用而言，顶层 const 在右边，底层 const 在左边。对于其他类型，全都是顶层 const**

```cpp
const int* const p3 = p2; // 从右向左读，右侧const是顶层const，表明p3是一个常量，左侧const是底层const，表明指针所指的对象是一个常量 
const int* p2 = &c;       // 这是一个底层const，允许改变 p2 的值 
int* const p1 = &i;       // 这是一个顶层const，不能改变 p1 的值          
```

执行对象的拷贝操作时，不能将底层 const 拷贝给非常量，反之可以，非常量将会转化为常量。



**练习** **2.30** **：**对于下面的这些语句，请说明对象被声明成了顶层const还是底层const？

const int v2 = 0; int v1 = v2; 

int *p1 = &v1, &r1 = v1; 

const int *p2 = &v2, *const p3 = &i, &r2 = v2; 

**解答：**

```
v2 和 p3 是顶层const,分别指向常量和常量指针
p2 和 r2 是底层const,指向常量 
```

**练习** **2.31** **：**假设已有上一个练习中所做的那些声明，则下面的哪些语句是合法的？请说明顶层 const 和底层 const 在每个例子中有何体现。

r1 = v2; 

p1 = p2; p2 = p1; 

p1 = p3; p2 = p3; 

**解答**

```cpp
r1 = v2;  // 合法
p1 = p2;  // 非法，p1是普通指针，p2是常量指针（底层const）（需同为底层const 拷贝）
p2 = p1;  // 合法，
p1 = p3;  // 非法，
p2 = p3;  // 合法，
```

### **2.4.4 constexpr和常量表达式**

>  常量表达式（const expression）: 指值不会改变并且在编译过程就能得到计算结果的表达式。

**字面值属于常量表达式**，由常量表达式初始化的 const 对象也是常量表达式。

```cpp
const int a = 32;          // 是常量表达式 
const int b = a + 1;       // 是常量表达式 
const int sz = get_size(); // 不是常量表达式，因为虽然 sz 是常量，但它的具体值等到运行时才知道。
```

#### **cosntexpr变量**

> C++新标准，用constexpr关键字类验证变量的值是否是一个常量表达式

```cpp
constexpr int sz = size(); //只有当 size() 是一个 constexpr 函数时这才是一条正确的声明语句  
constexpr int mf = 20;	   //20是常量表达式
constexpr int limit = mf + 1; // mf + 1 是常量表达式 
```

#### **字面值类型**

> 声明constexpt时用到的类型必须有所限制，这些类型为字面值类型。

包括：算术类型、引用、指针

- cosntexpr 指针的初始值必须是 nullptr 或 0 或存储于固定地址的对象。

- 函数体之外的对象和静态变量的地址都是固定不变的。

**指针和constexpr**

注意区分 constexpr 和 const 。constexpr 都是顶层 const，仅对指针本身有效。

```cpp
const int *p = nullptr;     // p 指向常量的指针 
constexpr int *q = nullptr; // q 常量指针，constexpr把它所定义的对象置为了顶层const  
```

**区分const和constexpr**

constexpr 限定了变量是**编译器常量**，即变量的值在编译器就可以得到。

const 则并未区分是编译器常量还是运行期常量。即 const 变量可以在运行期间初始化，只是初始化后就不能再改变了。

**constexpr 变量是真正的“常量”**

而 const 现在一般只用来表示 **“只读”**。

#### 成员函数+const

- 判断成员函数是否是const的，可以对其进行重载。作用是修改隐式this指针的类型

- this指针是一个系统送给我们的A *const类型的指针（A为类） 如果是常成员函数的话，系统送的这个this指针会再加一个限制，变成A const* const类型
- 当声明一个非静态成员函数为const时，对this指针会有影响。对于一个Test类中的const修饰的成员函数，this指针相当于Test const *, 而对于非const成员函数，this指针相当于Test* .

**const成员函数内只能读取类的数据成员，无法修改类的数据成员** **const成员函数内，不能调用其他非const成员函数** 这个特性被用来保证某些成员函数在实现过程中，避免由于程序员大意而对数据进行了错误的修改； 为什么要把const关键字放在参数列表后面，而不是放在前面呢？因为放在参数列表前面就成了修饰成员函数的返回值

**const的用法。如果const成员函数想要改变成员变量怎么办?**

方法一：mutable，如果不加mutable，i是没办法在func中更改的

```cpp
class C {
    public :
        void func(const int &p) const {
            i = p;
        }
        void show() {
            cout << i << endl;
        }
    private:
        mutable int i;
};

int main() {
    C c;
    c.func(2);
    c.show();
    return 0;
}
```

**方法二**：

```cpp
 const_cast(&cd)->op();
```

 **const的使用方法可以总结为4句话:**

- const 修饰某个非指针类型变量，表示该变量只读。
- const 修饰指针，在*号前面表示指针指向的内容不可更改，指针本身可以改变。
- const 修饰指针，在*号后面表示指针本身不可改变(不能被赋值)，指针指向的内容可以改变，这个指针必须在初始化的时候赋值。
- const 修饰成员函数，表示一个常量对象可以调用该成员函数。

**const和define的区别**

const 是常量数据类型，存处在程序的数据段，define只是进行文本的替换，存在与程序的代码区 角度1： 就定义常量说的话： const 定义的常数是变量 也带类型， #define 定义的只是个常数 不带类型。 角度2： 就起作用的阶段而言： define是在编译的预处理阶段起作用，而const是在 编译、运行的时候起作用。 角度3： 就起作用的方式而言： define只是简单的字符串替换，没有类型检查。而const有对应的数据类型，是要进行判断的，可以避免一些低级的错误。 正因为define只是简单的字符串替换会导致边界效应，具体举例可。

**练习** **2.32** **：**下面的代码是否合法？如果非法，请设法将其修改正确。

int null = 0, *p = null; 

**解答**

```cpp
int null = 0, *p = null;  // 非法，null是int变量，p是int指针，二者不能直接绑定.
应该改为:
int null =0, *p = &null  
```

## **2.5 处理类型**

### **2.5.1 类型别名**



有两种方法定义**类型别名**, 。

```cpp
typedef double wages;  // 传统方法使用 typedef 关键字 
using wages = double;  // 新标准使用 using 关键字进行别名声明       
```

typedef 作为声明语句中的基本数据类型的一部分出现。含有 typedef 的声明语句定义的不再是变量而是类型别名。和其他声明语句一样，typedef 的声明语句中也可以包含类型修饰符，从而构造符合类型。

```cpp
typedef double wages;
using SI = Sales_item;
int main() {
    wages hour, week;  // 等价于double hourly,weekly; 
    SI item;
    return 0;
}       
```

#### **指针、常量和类型别名**

如果是用某个类型别名指代复合类型，会产生意想不到的效果

```cpp
typedef char* pstring;  
const pstring cstr = 0; // 注意：const 是一个指向 char 的常量指针。
                        // 不能采用直接替换的方式将其理解为 const char* cstr = 0，这是错误的。 
```

### **2.5.2 auto类型说明符**

auto让编译器通过初始值来推算变量的类型

> 使用auto声明的变量的语句中，一句只能有一个基本数据类型

**复合类型、常量和auto**

编译器推断出的 auto 类型有时和初始值并不一样，编译器会进行适当的调整：

1. auto 根据引用来推断类型时会以引用对象的类型作为 auto 的类型。
2. auto 一般会忽略掉顶层 const，因此对于非指针类型的常量对象，auto 推断出的结果是不含 const 的。如果希望 auto 是一个顶层 const，需要明确指出。
3. auto 会保留底层 const。

概括一下就是 auto 会忽略引用与**顶层 const**。

```cpp
const int ci = 1, cr = ci; auto b = ci;       // b 是一个普通的 int。 
auto c = cr;       // c 是一个普通的 int。 
const auto d = ci; // d 是一个 const int 
auto &e = ci;      // e 是一个常量引用（常量引用是底层 const）。注意这个微妙的地方。 
auto f = &ci;      // f 是一个 const int*（位于左边的 const 是底层 const）   
```

int 与 int *、int & 是一个基本数据类型，而 const int 与 int 不是一种类型。

用 auto 定义引用时，必须用 & 指明要定义的是引用。



**练习** **2.33** **：**利用本节定义的变量，判断下列语句的运行结果。

a = 42; b = 42; c = 42; 

d = 42; e = 42; g = 42; 



**练习** **2.34** **：**基于上一个练习中的变量和语句编写一段程序，输出赋值前后变量的内容，你刚才的推断正确吗？如果不对，请反复研读本节的示例直到你明白错在何处为止。

**解答：**

编写一段程序

```cpp
#include <iostream>
int main()
{
    int i = 0, &r = i;
    auto a = r; // a 是一个整数（r 是 i 的别名，而 i 是个整数）
    const int ci = i, &cr = ci;
    auto b = ci; // b 是一个整数（ci 的顶层 const 特性被忽略掉了）
    auto c = cr; // c 是一个整数（cr 是 ci 的别名，ci 本身是一个顶层 const）
    auto d = &i; // d 是一个整型指针（整数的地址就是指向整数的指针）
    auto e = &ci; // e是一个指向整型常量的指针（对常量对象取地址是一种底层const）
    auto &g = ci; // g 是一个整型常量引用，绑定到 ci 
    std::cout << a << " " << b << " " << c << " " << d << " " << e <<
              " " << g << std::endl;
    a = 42;
    b = 42;
    c = 42;
    //d = 42; // 错误：d 是一个指针，赋值非法
    //e = 42; // 错误：e 是一个指针，赋值非法
    //g = 42; // 错误：g 是一个常量引用，赋值非法
    std::cout << a << " " << b << " " << c << " " << d << " " << e <<
              " " << g << std::endl;
    return 0;
}
```

**练习** **2.35** **：**判断下列定义推断出的类型是什么，然后编写程序进行验证。

const int i = 42; 

auto j = i; const auto &k = i; auto *p = &i; 

const auto j2 = i, &k2 = i; 

**解答**

```

```



### **2.5.3 decltype类型指示符**

> 希望从表达式的类型推断出要定义的变量的类型

```cpp
int f() {
    return 1;
}
int main() {
    decltype(f()) sum = 0;
    cout << sum << endl;
    return 0;
}
```

引用从来都是作为对象的别名出现，只有在 decltype 处是例外。

**decltype 和引用**

如果 decltype 使用的表达式不是一个变量，则 decltype 返回**表达式结果对应的类型**。可以使用这种方式来保证不获取引用类型。

注意**解引用指针的结果**是一个引用类型。**给变量加括号的结果**也是引用类型。**赋值操作的结果**也是引用类型。

```cpp
int i = 42, &r = i, *p; decltype(r+0) b;     // b 的类型是 int，因为 r+0 的结果类型是 int。   decltype(*p) c = i;   // c 的类型是 int&。
decltype((i)) d = i;  // d 的类型是 int&。    
```

decltype((var)) 的结果永远是引用，而 decltype(var) 的结果只有当 var 本身就是引用时才是引用。

## **2.6 自定义数据结构**

### **2.6.1 定义sales_data类型**

使用struct开始，紧跟类名和实体，类体由花括号包围形成一个新的作用域，⭐要加分号

struct+类名+类体+**分号。**类体可以为空。

```cpp
 struct Sales_data{};   // 注意：结尾加分号        
```

#### 类数据成员

> 每个对象都有自己的一份数据成员拷贝

C++11 新标准规定，可以为数据成员提供一个类内初始值，没有初始值将被默认初始化

### 2.6.2 使用Sales_data类

```cpp
struct Sales_data {
    string bookNo;
    unsigned units_sold = 0;
    double revenue = 0.0;
};
int main() {
    Sales_data data1, data2;
    double price = 0;
    //ISBN 销售数量 单价
    cin >> data1.bookNo >> data1.units_sold >> price;
    data1.revenue = data1.units_sold * price;  
    //data2
    cin >> data2.bookNo >> data2.units_sold >> price;
    data2.revenue = data2.units_sold * price;
    return 0;
}
```

**练习** **2.41** **：**使用你自己的 Sales_data 类重写 1.5.1 节（第 20 页）、1.5.2 节（第21 页）和 1.6 节（第 22 页）的练习。眼下先把 Sales_data 类的定义和 main 函数放在同一个文件里。

**解答：**

```cpp
//1.5.1-1.5.2
struct Sales_data {
    string bookNo;
    unsigned units_sold = 0;
    double revenue = 0.0;
    string isbn() { return bookNo; }
};
int main() {
    Sales_data data1, data2;
    double price = 0;
    //ISBN 销售数量 单价
    cin >> data1.bookNo >> data1.units_sold >> price;
    data1.revenue = data1.units_sold * price;  
    //data2
    cin >> data2.bookNo >> data2.units_sold >> price;
    data2.revenue = data2.units_sold * price;
    if (data1.isbn() == data2.isbn()) {
        double total_revenue = data1.revenue + data2.revenue;
        unsigned totalCnt = data1.units_sold + data2.units_sold;
        cout << data1.isbn()<< " " << totalCnt << " " << total_revenue << endl;
        return 0;
    }
    else {
        cout << "Not the same ISBN" << endl;
        return 0;
    }
    return 0;
}

//1.6
struct Sales_data {
    string bookNo;
    unsigned units_sold = 0;
    double revenue = 0.0;
    string isbn() { return bookNo; }
};
int main() {
    Sales_data total;
    string ID;
    unsigned count = 0;
    double price = 0.0;
    if (cin >> ID >> count >> price) {
        total.bookNo = ID;
        total.units_sold = count;
        total.revenue = price*count;
        while (cin >> ID >> count >> price) {
            if (ID == total.isbn()) {
                total.revenue += count * price;
                total.units_sold += count;
            }
            else {
                cout << total.isbn() << " " << total.units_sold << " " << total.revenue;
            }
        }
        cout << total.isbn() << " " << total.units_sold << " " << total.revenue;
    }
    else {
        cout << "NO data" << endl;
    }
    return 0;
}
```



### **2.6.3 编写自己的头文件**

- 类通常定义在头文件中，类所在头文件的名字应与类的名字一样。

- 头文件通常定义那些**只能被定义一次的实体**，比如类、const、constexpr 等。

- 头文件一旦改变，相关的源文件必须重新编译以获取更新过的声明。

有必要在书写头文件的时候做适当处理，使其遇到多次包含的情况也能安全和正常工作

> 比如一个头文件用了string文件，使用头文件的文件也要用string文件，这个使用的文件两次包含了string头文件

#### **预处理器概述**

> 能够确保头文件多次包含仍能安全工作，编译之前执行的程序。

#### 头文件保护符

> 其依赖预处理变量，有两种状态：已定义和未定义。一般把预处理变量的名字全部大写。

1. **\#define：**把一个名字设定为预处理变量

2. **\#ifndef：**当且仅当变量已定义时为真，一旦检查结果为真，则执行后续操作直到遇到 #endif 为止

3. **\#endif：**结果为真后，执行后续操作到#endif停止

4. **#ifdef** 当且仅当变量已定义时为真

   

## **2.7 问题集**

1. 指针和引用有4点不同，分别是哪些？
2. const 对象必须怎样
3. const 对象的作用范围
4. **什么是常量引用，如何声明，是顶层还是底层**
5. 常量引用与常量对象、非常量对象的关系。
6. **什么是常量指针，如何声明，是顶层还是底层**
7. 常量指针与常量对象、非常量对象的关系。
8. 顶层 const 和底层 const 都是什么，在什么位置
9. **如何区分顶层 const 和底层 const**
10. constexpr 是什么，特点是什么

**回答**

1. 指针是对象而引用不是；指针可以重定向引用不可以；有指向指针的指针无引用的引用；引用必须初始化指针不需要
2. 必须初始化
3. 默认范围是文件内
4. **不能改变对象的引用是常量引用，const int& i = a，是底层 const**
5. 不能用非常量引用绑定常量对象，可以用常量引用绑定非常量对象。
6. **常量指针表明指针是个常量，其内存储的地址不能改变，但是指针还能修改所指对象的值。int\* const p = a，是顶层const。**
7. 可以用常量指针指向非常量对象。
8. **顶层 const 表示指针本身是常量，底层 const 表示所指对象是常量****。顶层 const 在右边，底层 const 在左边**
9. **只有指针同时有顶层和底层，const 在星号右边是顶层，左边是底层。引用的 const 是底层，其他类型 const 是顶层。**
10. 常量表达式。两个点：值不能改变、**在编译阶段就可以计算出值**

**问题**

1. 浮点数赋给整型变量时如何舍入？
2. decltype 是什么，如何使用
3. 如何声明而非定义一个变量
4. 如果指针不初始化会有什么影响
5. 如何在多个文件间共享 const 对象
6. 使用 auto 来定义引用时要注意什么
7. 预处理变量的作用范围是什么
8. C++属于静态类型语言，静态类型语言的含义是什么？
9. C++有两种定义类型别名的方式，分别是什么

**回答**

1. 只保留小数点前的部分，即向零舍入
2. 用来获取变量类型，decltype(c) a;
3. 使用 extern 修饰符： extern int i:
4. 在块作用域中，未初始化的指针的值是未定义的。
5. 如果想在多个文件间共享const对象，必须在变量的定义前添加**extern**关键字并在本文件中声明。**声明和定义都要加extern**
6. 用 auto 定义引用时，必须要加 & 符号。尤其是在范围 for 循环中，当想要修改值时，一定要记得加上引用符。
7. 文件内。
8. 静态类型语言在编译时检查变量类型。
9. typedef unsigned int size_type 和 using size_type = unsigned int;



## 2.8 参考资料

1. https://zhuanlan.zhihu.com/p/412368237
2. https://zhuanlan.zhihu.com/p/454873031