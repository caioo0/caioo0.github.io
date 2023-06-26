**问题**

1. 使用加号连接字符串/string时要注意什么
2. string 的索引是什么类型，s.size() 返回什么类型。
3. 如何方便地判断 string 中的某个字符的类型（比如是数字还是字母）以及转换某个字符的大小写。
4. 值初始化的结果是怎样的
5. 定义 c 风格数组时数组维度的限制条件
6. 如何使用数组来初始化 vec
7. string 类型可以隐式转化为 c 风格字符串（即字符数组）吗？
8. 如何将 string 类型转化为 c 风格字符串
9. 使用 getline() 函数从输入流读取字符串存到 string 中，存储的内容有换行符吗？
10. 使用范围for循环要注意什么？

**回答**

1. 加号两边至少有一个是 string 类型，不能都是字符串
2. 都是 string::size_type 类型，是无符号值。
3. 使用 **cctype** 头文件中的 isalnum(),  isalpha(), isdigit(), isupper(), islowwer(), ispunct(), isspace(), tolower(), toupper() 等类型。
4. 值初始化会将内置类型初始化为 0，类类型由类自己来默认初始化。
5. **维度必须是个常量表达式，即在编译阶段就可以确定值**。（因为数组维度是数组的类型的一部分，而 **C++ 是静态语言，即在编译阶段就要确定类型**）
6. vector vec(begin(arr),end(arr));
7. 不可以（从 C 风格字符串到 string 的转换是用了 string 的转换构造函数，而 string 并没有定义到 C 风格字符串的类型转换运算符）
8. 使用 c_str() 函数
9. 没有换行符。
10. 如果要修改循环变量的值要将其声明为引用类型：auto &

**问题**

1. 如果容器为空，begin() 的返回值是什么？
2. 使用数组时要注意数组维度的什么特点？
3. 区分 int *ptrs[10]; int (*ptrs)[10]; int (&ptrs)[10] 的不同含义
4. C风格字符串属于什么类型？

**回答**

1. 返回的是尾后迭代器，和 end() 的返回值一样。
2. 使用数组时注意数组的维度必须是个常量表达式，因为数组的维度也属于数组类型的一部分，而编译器在编译阶段就需要知道数组类型。
3. 他们分别定义了：一个包含10个整型指针的数组，一个指向包含10个整型值的数组的指针，一个包含10个整型值的数组的引用。
4. C风格字符串本身不是类型，而是一种写法，它的类型是字符数组。**要从字符数组的角度来理解C风格字符串的各项操作。**

**第3章 字符串、向量和数组**

string、vector是两种最重要的标准库类型，迭代器是一种与 string 和 vector 配套的标准库类型。

内置数组和其他内置类型一样，数组的实现和硬件密切相关，因此与string和vector相比，数组在灵活性上稍显不足。

**3.1 命名空间的using声明**

可以对单个名字进行独立的using声明

​                using std::cin;              

**头文件里不应包含 using 声明**

**3.2 标准库类型string**

string 表示可变长的字符序列。

string 定义在命名空间 using 中。  

**3.2.1 定义和初始化string对象**

string 默认初始化为一个空的 string。

​                string s1;       //将 s1 默认初始化为一个空的 string string s1(s2);   //使用拷贝构造函数进行的拷贝初始化。s1 是 s2 的拷贝。 string s1 = s2;  //使用拷贝赋值运算符进行的拷贝初始化。s1 是 s2 的拷贝。 string s1("value");  //s1 是字面值 "value" 去除最后一个空字符后的拷贝。 string s1 = "value"; //同上。 string s1(n,'c'); //s1 初始化为 n 个 'c'。              

注意：使用字符串字面值或字符数组初始化 string 对象时，string 对象中是不包含末尾的空字符的，它会将字符数组中末尾的空字符去掉。

**初始化方式**

拷贝初始化：使用等号

直接初始化：不使用等号

列表初始化：使用花括号{}

**3.2.2 string对象上的操作**

​                getline(is, s2);//从输入流 is 中读取一行赋给 s2，is 是输入流。 s.empty();//s为空则返回 ture s.size(); //返回字符数，类型为 size_type，无符号整数 s[n];     //对 s 中元素的索引 s3 = s1 + s2;//连接 s1 与 s2，加号两边必须至少有一个是 string，不能都是字面值，比如 "world"+"hello" 是错误的 <.<=,>,>=;   //比较时从前往后比较单个字母的大小              

因为 cin 会**自动忽略开头的空白并遇到空白就停止读取**，因此不能使用 cin 读取句子；

字符串字面值与 string 是两种不同的类型

**读写string对象**

可以使用 cin, cout 来读写 string 对象，也可以使用 stringstream 来读写 string 对象。

**getline 函数**

getline() 定义在**头文件 string** 中，以一个 istream 对象和一个 string 对象为输入参数。getline() 读取输入流的内容直到遇到换行符停止，然后将读入的数据存入 string 对象。

注意 getline 会将换行符也读入，但是不将换行符存入 string 对象。**即触发 getline() 函数返回的那个换行符实际上被丢弃掉了。**

getline() 只要一遇到换行符就结束读取操作并返回结果，即使一开始就是换行符也一样，这种情况下会得到一个空 string。

**getline() 与 << 一样，会返回它的流参数。**所以可以用 getline 的结果作为条件。

**string::size_type 类型**

string 的 size() 成员函数返回一个 string::size_type 类型的值。

大多数标准库类型都定义了几种配套的类型，这些**配套类型体现了标准库与机器无关的特性**。

在具体使用时，通过作用域操作符来表明 size_type 是在类 string 中定义的。

string::size_type 是**无符号值**，可以确定的是它足够存放任何 string 对象的大小。

C++11 允许通过 auto 和 decltype 来获得此类型。

​                auto len = s.size();// len 的类型是 string::size_type              

不要在同一个表达式中混用 size_type 和 int 类型。

**3.2.3 处理string对象中的字符**

**cctype 头文件**中有下列标准库函数来处理 string 中的字符。

下面这些函数的输入和返回值实际都是 int 类型的，且**输入的值 c 必须满足 -1<=c<=255**，**即输入必须是 ASCII 字符。**

​                int isalnum(int c);  // 当c是字母或数字时为真 isalpha(c);  // 当c是字母时为真 isdigit(c);  // 当c是数字时为真 islower(c);  // 当c是小写字母时为真 isupper(c);  // 当c是大写字母时为真 ispunct(c);  // 标点符号 isspace(c);  // 空白（包括空格、制表符、回车符、换行符等） tolower(c);  // 字符转换为小写，返回转换结果 toupper(c);  // 字符转换为大写，返回转换结果 '应用' tolower(string[4]);              

建议：使用 c++ 版本的标准库头文件，即 cname 而非 name.h 类型的头文件。cname 头文件中的名字都从属于命名空间 std；

**范围for语句**

​                string str; for(auto c:str)         // 对于str中的每个字符    cout << c << endl;  // 输出当前字符，后面紧跟一个换行符              

当要改变 string 对象中的值时，需要把循环变量定义成**引用类型**。必须通过显示添加 & 符号来声明引用类型。

不能在范围 for 语句中改变所遍历序列的大小。

​                for(auto &c:str)    c = toupper(c);     // 转换为大写              

对 string 的最后一个字符进行索引：s[s.size()-1];

索引必须大于等于 0 小于 size，使用索引前最好用 if(!s.empty()) 判断一下字符串是否为空。

任何表达式只要是整型值就可以作为索引。索引是无符号类型 size_type；

**3.3 标准库类型vector**

vector 是一个类模板

vector 是模板，vector 是类型

**3.3.1 定义和初始化vector对象**

vector 默认初始化为一个空 vector。

​                vector<string> v2(v1);       // v2=v1 vector<string> v3(10,"hi");  // 10个string vector<string> v4(10);       // 10个空string vector<string> v5{"an","the"};  // 列表初始化              

**值初始化**

**值初始化的方式：**如果对象是内置类型，则初始值为 0，如果是类类型，则由类默认初始化。

**列表初始化**

使用花括号一般表示列表初始化：初始化过程会尽量把花括号内的值当作一个初始值列表来处理。

如果花括号内的值不能用来列表初始化，比如对一个 string 的 vector 初始化，但是花括号内的值为整型，如下：

​                vector<string> v {10};        // v 有 10 个默认初始化的元素 vector<string> v {10, "hi"};  // v 有 10 个值为 "hi" 的元素              

**3.3.2 向vector对象中添加元素**

vector可以高效增长，通常先定义一个空 vector，然后在添加元素会更快速。

定义 vector 时，已知 vector 的大小，如果初始值都一样，初始化时确定大小与值会更快。如果初始值不全一样，即使已知大小，最好也先定义一个空的 vector，再添加元素。

**3.3.3 其他vector操作**

​                v.size(); v.empty(); v.push_back(t);              

可以用范围 for 语句处理 vector 序列的元素

**3.4 迭代器介绍**

所有标准库容器都可以使用迭代器

**3.4.1 使用迭代器**

​                auto b = v.begin(), e = v.end(); auto d = v.cbegin(); f = v.cend();  // 返回的是const_iterator              

end 成员指向容器的”尾后元素“

如果容器为空，则 begin 和 end 返回的都是尾后迭代器

​                *iter     // 返回iter所指元素的引用 iter->mem // 等价于 (*iter).mem ++iter    // 指向下一个元素              

迭代器的类型是 iterator 或 const_iterator 来表示

​                vector<int>::iterator it = v.begin(); string::iterator it;              

**3.4.2 迭代器运算**

string 和 vector 支持的迭代器运算。注意不能将两个迭代器相加。

​                iter + n; iter += n; iter1 - iter2; // 返回两个迭代器之间的距离，difference_type类型的带符号整数 >, >=, <, <=;  // 比较运算符              

**3.5 数组**

数组的大小确定不变

**3.5.1 定义和初始化内置数组**

​                int a[10];  // 数组的维度必须是个常量表达式              

数组和 vector 的元素都必须是对象，不能是引用

数组不能用 auto 来定义。

**字符数组的特殊性**

​                char a1[] = {'c', '+', '+'};  // 列表初始化，没有空字符，维度是3 char a2[] = "c++";            // 有空字符，维度是4 const char a4[3] = "c++";     // 错误，没有空间存放空字符              

不能用数组为另一个数组赋值或拷贝。可以按元素一个一个拷贝，但**不能直接拷贝整个数组**。

按照由内向外的顺序理解数组的类型                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         

​                int *ptrs[10];           // ptrs是一个含有10个整型指针的数组 int (*ptrs)[10] = &arr;  // ptrs是一个指针，指向一个含有10个整数的数组 int (&ptrs)[10] = &arr;  // ptrs是一个引用，引用一个含有10个整数的数组              

**3.5.2 访问数组元素**

数组下标通常用 size_t 类型

使用范围 for 语句遍历数组元素

**3.5.3 指针和数组**

在大多数情况，使用数组类型的对象其实是使用一个指向该数组首元素的指针

标准库类型（如 string、vector 等）的下标都是无符号类型，而数组内置的下标没有这个要求。

指向数组元素的指针等价于 vector 中的迭代器

**3.5.4 C风格字符串**

c++ 支持 c 风格字符串，但是最好不要使用，c 风格字符串使用不便，并且极易引发程序漏洞

c 风格字符串不是一种类型，而是一种**写法**，是为了表达和使用字符串而形成的一种约定俗成的写法。

用这种写法书写的字符串存放在字符数组中并以**空字符（'\0'）**结束。

**c 风格字符串函数**

​                strlen(p);       // 返回 p 的长度，不包括空字符 strcmp(p1, p2);  // 比较 p1 与 p2，如果 p1 大于 p2，返回一个正值，如果相等返回 0，否则返回负值。 strcat(p1, p2);  // 把 p2 附到 p1 之后，并返回 p1 strcpy(p1, p2);  // 把 p2 拷贝给 p1，返回 p1              

这些函数都不验证参数。传入参数的指针必须指向以空字符结束的数组。必须确保数组足够大。

​                char ca[] = {'q','b','d'};  // 使用列表定义的都没有空字符              

对于 string，可以使用 s = s1 + s2，s1 > s2 等加和与比较，而 c 风格字符串不行，因为他们实际上是指针。

**3.5.5 与旧代码的接口**

**string对象和C风格字符串的混用**

可以使用字符串字面值来初始化 string 对象或与 string 对象加和，所有可以用字符串字面值的地方都可以使用以空字符结束的字符数组来代替。

反过来不能使用 string 对象初始化字符数组，必须要用 **c_str()** 函数将 string 对象转化为 c 风格字符串

​                const char* cp = s.c_str();  // s.c_str() 返回一个指向以空字符结束的字符数组的指针。              

**使用数组初始化 vector 对象**

可以使用数组来初始化 vector 对象，用两个指针来表明范围（左闭合区间）

​                int arr[] = {0, 1, 2, 3, 4, 5}; vector<int> ivec(begin(arr), end(arr));              

**建议不要使用 c 风格字符串和内置数值，都使用标准库容器**

**3.6 多维数组**

严格来说 C++ 中没有多维数组，那实际是数组的数组。

​                int arr[10][20][30] = {0};  // 将所有元素初始化为 0              

**多维数组的初始化**

​                '显式初始化所有元素' int arr[2][3] = {1,2,3,4,5,6}; int arr[2][3] = { {1,2,3},{4,5,6} };//上面这两种方式效果是一样的 '显式初始化部分元素' int arr[2][3] = { {1},{4,5} };//将第一行第一个元素和第二行第一、二个元素初始化为1,4,5，其他元素执行值初始化。              

**多维数组的下标引用**

​                int arr[2][3]; arr[0];//这是一个有三个元素的一维数组 arr[0][0];//第一行第一列的元素              

**使用范围 for 语句处理多维数组**

新标准中可以使用范围 for 语句处理多维数组。

注意范围 for 语句中改变元素值要显示使用 & 符号声明为引用类型。

注意：使用范围 for 循环处理多维数组时，**除了最内层的循环外，其他所有循环的控制变量都应该是引用类型**。

因为如果不声明为引用类型，编译器会自动将控制变量转换为指向数组首元素的指针，就不能在内层继续使用范围 for 循环处理该控制变量了。

​                for(auto& row : arr)    for(auto col : row)              

**使用 3 种方式来输出 arr 的元素**

​                // 范围 for 语句-不使用类型别名 for (const int (&row)[4] : arr)   for (int col : row)     cout << col << " "; cout << endl; // 范围 for 语句-使用类型别名 using int_array = int[4]; for (int_array &p : ia)   for (int q : p)     cout << q << " "; cout << endl; // 普通 for 循环 for (size_t i = 0; i != 3; ++i)   for (size_t j = 0; j != 4; ++j)     cout << arr[i][j] << " "; cout << endl; // 指针 for (int (*row)[4] = arr; row != arr + 3; ++row)   for (int *col = *row; col != *row + 4; ++col)     cout << *col << " "; cout << endl;              