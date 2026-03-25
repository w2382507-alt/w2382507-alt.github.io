# #coding

- <https://ailab.bnu.edu.cn/>
- 有关于软件工程

  - 游戏开发

    - 顺序

      - 1、读取操作
      - 2、处理数据
      - 3、绘制画面
      - 先搭大结构，细节用注释代替
  - 一些实现方法

    - 一个变量的值在n种值之间循环：i++，i % n
    - 动态延时

      - DWORD start\_time = GetTickCount();
      - DWORD end\_time = GetTickCount();
      - DWORD delta\_time = end\_time - start\_time;
      - if (deltatime < 1000 / n) Sleep(1000 / n - delta\_time);

        (锁n帧)
    - n进制下的操作

      - 去除最后一位数 / n

        - 或表示为[x/n]
      - 取出最后一位数 % n
    - 完美输入

      - - ![](https://api2.mubu.com/v3/document_image/1970090_90264372-a3ba-4948-b0ec-d3940248df82.png)
      - - ![](https://api2.mubu.com/v3/document_image/1970090_fb85e5aa-0eec-41f4-ff49-05bc7bc951cc.png)
- 注释

  - // 本行后为注释
  - /\*\*/ 中间为注释
- 头文件

  - # include <头文件名>
  - c/c++

    - stdio.h
    - string.h/cstring

      - strlen( )

        - 参数：指向以\0结尾的C字符串的指针
        - 返回值：字符串长度（不包括空字符）
      - strcpy(charr1, charr2)

        - charr2复制到charr1中
        - 将源头的字符串拷贝到目的地字符串中，包括null字符，并在该点停止
      - strcat(charr1, charr2)

        - charr2附加到charr1末尾
      - strcmp(charr1, charr2)

        - 如果两个字符串相同，该函数将返回零
        - 如果第一个字符串排在第二个字符串之前，则返回一个负数值
        - 如果第一个字符串排在第二个字符串之后，则返回一个正数值
        - charr1 - charr2
    - time.h/ctime

      - clock( )

        - 返回程序开始执行后所有的系统时间
        - 将clock\_t作为clock( )返回类型的别称
      - CLOCKS\_PER\_SEC

        - 符号常量
        - 等于每秒钟包含的系统时间单位数
    - Windows.h

      - void Sleep(DWORD ms)

        - Sleep函数可以使计算机程序（进程，任务或线程）进入休眠
        - 毫秒为单位
      - DWORD GetTickCount(void);

        - 返回从操作系统启动到现在所经过的毫秒数
      - DWORD

        - typedef unsigned long DWORD;
        - 四个字节无符号整型
    - ctype.h/cctype

      - - ![](https://api2.mubu.com/v3/document_image/1970090_90dedfab-16a4-4792-d4f6-6d249ef5d86f.png)
    - stdbool.h

      - bool类型所在头文件
    - stdlib.h/cstdlib

      - int rand(void)

        - 生成一个伪随机整数0~RAND\_MAX
        - 范围 [a,b] : rand() % (b - a + 1) + a
    - math.h/cmath

      - double pow(double x, double y)

        - 返回 x 的 y 次幂
      - double sqrt(double x)

        - 返回 x 的平方根
  - c++

    - iostream
    - fstream
    - @string
    - @vector
    - @array
- 名称空间

  - 类、函数和变量便是C++编译器的标准组件，它们现在都被放置在名称空间std中
  - using namespace std;后可省略std::
  - using std::cout; 后可省略cout变量的std::
- 输入/输出

  - 转义字符

    - - ![](https://api2.mubu.com/v3/document_image/1970090_510b52a4-d263-448c-d1c6-9a33d59dfe60.png)
    - - ![](https://api2.mubu.com/v3/document_image/49e8a7a2-b90c-44c2-9e22-57488a2eae84.png)
  - c++语言

    - 输出

      - cout

        - std::cout << 变量

          - cout 对象表示输出流
          - <<插入运算符
        - cout << char变量 或 ‘字符’ 输出为 字符
        - cout << char地址 @输出字符串
        - 字符串拼接

          - 将两个用引号括起的字符串合并为一个
          - 任何两个由空白（空格、制表符和换行符）分隔的字符串常量都将自动拼接成一个
          - cout << "abcd" "efgh";
      - cout.put( )

        - 会将整数输出为字符
    - 输入

      - cin

        - std::sin >> 变量
        - cin >> char变量 输入的会识别为字符，给char变量一个整数（例如输入“5”会存储字符编码53）
        - 当cin>从缓冲区中读取数据时，若缓冲区中第一个字符是分隔符时，cin>>会将其 **忽略并清除**，继续读取下一个字符；若缓冲区为空，则**继续等待**。读取成功，字符后面的分隔符是残留在缓冲区
        - cin >> char地址@输入字符串
      - cin.getline(字符数组名， 字符数)

        - 抵达换行符时结束，**丢弃换行符**
        - 结尾自动加上’\0'，并且计入读取的字符数中
      - cin.get()

        - cin.get(ch)

          - 读取一个字符并赋给变量ch
        - cin.get(字符数组名，字符数）

          - 抵达换行符时结束，**不丢弃换行符**
        - cin.get( )

          - 读取一个字符，并返回其值
          - 可用与处理cin或cin.get()留下的换行符
      - 输入状态

        - cin.eof( )

          - 读取到文件末尾返回ture
          - Ctrl+Z和Enter模拟EOF
        - cin.fail( )

          - 输入操作失败返回ture
        - cin.good( ）
        - cin.bad( )
        - cin.clear( )
    - 文本输入/输出

      - 输出

        类似于string类

        - 1.# include <fstream>
        - 2.std::ofstream 对象名;
        - 3.对象名.open("文件名");

          - 如果文件不存在，将新建一个
          - 如果文件存在，则将原有内容覆盖
        - 4.就像cout一样使用ofstream对象
        - 5.对象名.close( );
      - 输入

        - 1.# include <fstream>
        - 2.std::ifstream 对象名;
        - 3.对象名.open("文件名");

          - 如果文件不存在，将新建一个
          - 如果文件存在，则将原有内容覆盖
        - 4.就像cin一样使用ifstream对象
        - 5.对象名.close( );
    - 换行

      - cout << std::endl
      - cout << '\n'
      - cout << "\n"
  - c语言

    - printf("格式控制字符串", 输出参数1, ..., 输出参数n);

      - 返回值

        - 如函数执行成功，则返回所打印的字符总数，如果函数执行失败，则返回一个负数
      - 格式控制符 %

        - %[flags][width][.precision][length]specifier,
        - 转换说明符 specifier

          - d/i -> 有符号十进制整形
          - u -> 无符号十进制整形
          - o -> 无符号八进制整形
          - x/X -> 无符号十六进制整形
          - f/lf -> 十进制浮点（默认精度6）
          - e/E -> 科学计数法表示的浮点数（默认精度6）
          - c -> 字符类型

            输入字符是空白符等不会被忽略
          - s -> 字符串（输出直到'\0'）数组名作为参数
          - p -> 十六进制指针
        - 标志 flags

          - - 左对齐

            右对齐在左侧补空格
            左对齐在右侧补空格
          - + 正数输出带正号
          - 空格 在值前插入一个空格
          - # 输出时带进制符号
          - 0 使用0填充
        - 最小宽度 width

          - 数字表示显示字段的宽度
          - 不足用空格补齐
          - 有flags：0用0补充
          - 有\*号 用参数作为宽度

            printf("%0\*d\n", 5, 6); 00006
        - 类型长度 length

          - h 短整型或无符号整型
          - l 长整型或无符号长整型或double
          - L long double
          - 对于输出变量时无特定要求，以变量类型为准
      - 字符串拼接

        - 1.需要换行的地方使用 **反斜杠+回车** 注意第二行必须从最左侧开始
        - 将多段内容放在不同的双引号内 两个双引号之间使用回车
    - scanf("格式控制字符串", 地址1, ..., 地址n);

      - 返回值

        - 如果读取成功，scanf() 将返回成功匹配并赋值的个数
        - 如果读取失败，或者达到文件末尾，或者遇到输入结束的条件，则返回 EOF
      - 格式控制符 %

        - %[\*][width][length]specifier
        - 赋值忽略符\*：使得该占位符不返回值，用于处理不需要的输入
        - 读取长度width：表示读取长度的最大值
        - 类型长度 length：与printf相同，但起作用
        - 转换说明符sprcifier：与printf相同

          - %c 类型如果前面没有空格、换行等则不会吸收，直接读取空格；所以要使用getchar来跳过换行符
          - %s 类型会在读取后自动添加'\0'，数组名作为参数，不用加&
          - %[] 读取输入中属于指定字符集合内的所有字符，直至遇到不在集合内的字符，不会自动添加'\0'
          - %[^ ]读取除指定字符之外的所有字符
      - 格式设置

        - 格式控制符之间有空格、回车、制表符

          - scanf是以 **空格、制表符、回车符 **为结束符
          - 格式控制符中的空格、制表符、回车符的作用是 **吸收**空格、制表符和回车符
        - 格式控制符之间有逗号，或者其它格式符号

          - 必须按照格式控制符中的格式输入数据
        - 结尾回车会被吸收吗
    - putchar()

      - int putchar(int character);
      - 将一个字符输出到标准输出，如果发生错误，则返回 EOF
    - getchar()

      - int getchar(void);
      - 读取成功时返回读取的字符（以int类型表示）；遇到文件结束（EOF）或错误时返回EOF（通常定义为 - 1）
- 赋值

  - 可连等
  - 从右向左赋值
  - 初始化

    - type name = ...
    - type name( ... )
    - type name = {...}
    - type name {...}

      { } 内无内容，初始值为0
    - auto声明

      - auto typeName = 初始值
      - 根据初始值默认类型设置变量类型
- 函数

  - 创建新函数

    - 提供函数定义

      - type functionname(parameterlist) {statements... return 返回值; }

        有返回值
      - void functionname(parameterlist) { statements }

        无返回值

        - 可以使用return; 退出函数
      - 函数在执行第一条返回语句后结束
    - 提供函数原型

      - 原型语句

        - double sqrt(double)**;**

          一定要加;
    - 调用函数
  - 库函数

    - 库文件（namespace）包含函数的编译代码，头文件（#include)包含原型
  - 函数参数

    - 参数内存

      - 函数被调用时，计算机为变量分配内存
      - 函数结束时，计算机将释放这些内存
    - 传递参数

      - 按值传递

        - 按值传递结构

          也可以按值返回结构
      - 按指针传递

        - 传递数组1 （函数名 ，元素个数）

          - 指向数组的指针 typeName pointName [] == typeName \* pointName

            此方法并不会传递数组的元素数量，该参数只是作为普通指针使用，还需要第二个参数传递数组长度
          - 不能在函数内被修改的指针 const typeName pointName [] == const typeName \* pointName
        - 传递数组2 （函数名，函数名+元素个数）

          - eg： int sum\_arr(const int \* begin, const int \* end); {const int \* pt = begin; ......}
        - 传递二维数组 （函数名（指明列数）， 行数）

          - int array[2][2]
          - int array[][2]
          - int (\*array) [2]

            一定要加括号，否则int \* array[2]被解释为一个数组，包括两个指向int类型的指针
          - 只能接受列数正确的二维数组
        - c-风格字符串

          - char数组
          - 字符串字面值
          - char \* 指针
        - 传递结构的地址

          - &结构名
      - 按引用传递
- 变量

  - 整型

    - 确定类型

      - 默认为int
      - 给数字添加后缀表示类型
      - long → L UL
      - long long → LL ULL
    - 字节长度

      - short → 2
      - int → 4 -32768～32767
      - long → 4
      - long long → 8
    - 字面值

      - |  | 表示法 | 控制符 |
        | --- | --- | --- |
        | 十进制 | 第一位1~9 | std::dec |
        | 八进制 | 第一位0 | std::oct |
        | 十六进制 | 0x.../0X... | std::hex |
      - std::cout << std::dec;
    - 头文件climits & 无符号类型

      - #include <climites>
      - |  | 无符号类型 | climits符号常量 |
        | --- | --- | --- |
        | char |  | **CHAR\_BIT** / **CHAR\_MAX** / **CHAR\_MIN** / **SCHAR\_MAX** / **SCHAR\_MIN** / **UCHAR\_MAX** |
        | short | unsigned short | **SHRT\_MAX** / **SHRT\_MIN** / **USHRT\_MAX** |
        | int | unsigned int / unsigned | **INT\_MAX /** **INT\_MIN /** **UINT\_MAX** |
        | long | unsigned long | **LONG\_MAX /** **LONG\_MIN** / **ULONG\_MAX** |
        | long long | unsigned long long | **LLONG\_MAX /** **LLONG\_MIN /** **ULLONG\_MAX** |
      - 有符号向上溢出，得到负最小值
      - 无符号向上溢出，得到0
    - 初始化

      - int n\_int = INT\_MAX;
      - int n\_int(INT\_MAX);
      - int n\_int = {INT\_MAX}; //大括号内无数据则初始化为零
      - int n\_int {INT\_MAX};
      - const 限定符

        - const 类型 变量名 = 数值;
        - 初始化后的值无法被改变
    - char 类型

      - ‘ M’ 单引号表示字符的数字编码
    - bool 类型

      - bool 变量名 = true/false;
      - true被转换为1，false被转换为0
      - 任何非零值被转换为true，0被转换为false
  - 浮点数

    - 书写

      - 小数点表示法：一定要加点几（例如8.0）

        - 可以省略整数，.5
        - 可以省略小数，5.
      - E表示法：+5.37E+16 （负号不可省略正号可省略、e或E都可）
    - 确定类型

      - 默认为double
      - 给数字添加后缀表示类型
      - float → f/F
      - long double → l/L
    - 精度

      - float → 6/7位
      - double → 15/16位
      - long double → 18
  - 类型转换

    - 初始化和赋值

      - a = b （a存储b的数值，a、b类型保持不变）
      - 浮点数赋值给整型，小数部分直接删除
    - { }方式

      - 不允许窄缩
    - 自动类型转换

      - ![](https://api2.mubu.com/v3/document_image/824d5c47-09fa-409b-a7c1-0ea0657f98b5.jpeg)

      - 水平方向自动执行
      - 竖直方向若同时存在则向上转换
    - 强制类型转换

      - *(typeName) value*
      - typeName (value）

        不推荐 必须写int i2 = int( (f1 + f2) );语法很易错
      - static\_cast<typeName> (value) （only c++）
  - string类（only c++）

    - @string 头文件 & std::名称空间
    - 赋值、拼接、附加

      - str1 = str2
      - str3 = str1 + str2
      - str1 += str2
    - string 类一定要加std::
    - string类不依赖\0判断结尾，只有在以c风格字符串赋值时会包含\0，所有不要用\0来判断结尾，正确的遍历方法是i < str.size()
    - str没法用str[i]来一个个赋值，因为可能存在越界风险，使用 += 给str增加字符
    - getline(cin, str); 给str输入一整行
- 复合类型

  - 数组array

    - 声明与初始化

      - typeName arrayName[arraySize] = {a1, a2, ..., an};
      - arraySize只能为整型常数或const值
      - arraySize为空，编译器自动通过初始化计算元素个数
      - 不完全初始化剩余元素默认为零

        不写=｛｝会导致数组没有初始化，不会自动设置为0，是随机值！
    - c-风格字符串

      - 以 '\0' 结尾的char数组
      - "abcd"为字符串常量，最后有隐藏的'\0'
      - cout 打印char地址 出发向后逐个字符打印知道遇到空字符'\0'为止 @输出字符串
      - cin 输入char地址 结尾回自动加上'\0' @输入字符串
      - 字符串数组不能用=赋值（只在初始化时可用） 要用strcpy() or strncpy()
    - @数组表示法

      - array\_name 本质是数组第一个元素的地址
      - arrayname = &arrayname[0]
      - arrayname[ i ] = \*(arrayname +1)
    - 二维数组

      - 声明

        - 类型名 数组名[行数][列数]；

          - 数组名的含义为：a是一个有行数个元素的指针数组，指向数组的指针，每个数组内有列数个元素
          - 类似于int (\*p) [4]
        - 由行细分到列
      - 初始化

        - 分段赋值

          - ｛｛｝,｛｝｝
        - 连续赋值
      - 访问

        - 数组名[行下标][列下标]
        - 遍历时利用嵌套循环，外层遍历行，内层遍历列
        - - ![](https://api2.mubu.com/v3/document_image/e4b02f9d-8cae-4773-af9c-f478a1819c9e.png)
    - 数组替代品（only c++）

      - vector

        - @vector std::
        - std::vector<typeName> vt (n\_elem);
        - n\_elem可以是变量
      - array

        - @array std::
        - std::array<typeName, n\_elem> arr;
        - n\_elem是整型常数或const值
        - 可以将一个array对象赋给另一个array对象
  - 结构struct

    - 声明

      - struct 结构类型名 {变量类型1 变量名1; 变量类型2 变量名2;...};
    - 初始化

      - 结构类型名 结构名 = {value1, value2, ...};
      - 可以将一个结构赋值给另外一个结构
    - 成员运算符( . )

      - 结构名.变量名
  - 公用体union

    - 声明

      - union 共用体类型名 {变量类型1 变量名1; 变量类型2 变量名2;...};
    - 共用体长度为其最大成员的长度
  - 枚举（only c++）enum

    - 声明

      - enum 枚举类型名称{枚举量1, 枚举量2, ...};

        - 第一个枚举量为0，往后依次加一
      - enum 枚举类型名称{枚举量1 = int, ...};

        - 指定的值必须是整数
        - 没有被初始化的枚举量的值比前面大1
    - 声明变量

      - 枚举类型名称 变量名
    - 只能将定义枚举时用的枚举量赋给这种枚举的变量

      - 赋值时不可用算术运算，会被转换为int类型
- 指针

  - 初始化

    - int \* pt = new int;
    - int \* pt = &valueName;
    - int \* pt = anotherPonit;
  - 指针类型转换

    - pt = (typeName \*) value;
  - new运算符( only c++)

    - 动态变量

      - typeName \* pointer\_name = new typeName;
    - 动态数组

      - typeName \* pointer\_name = new typeName [num];
      - @数组表示法 与 指针表示法

        - pointername[n] 表示第n+1个元素
        - pointername[ i ] = \*(pointername + 1)
        - arrayname[ i ] = \*(arrayname +1)
      - 指针算术

        - 指针与整数相加，结果为地址值加上 指向对象占用的字节数乘以整数
        - 指针相减得到整数，两个指针间的距离
        - 无法改变数组名所指的地址，但可以对其进行指针算术

          - arrayname + 1 将地址值加一个元素的内存
          - &arrayname + 1 将地址值加一个数组的内存
    - 动态结构

      - pt[1].name
      - \*(pt+1).name
      - (pt+1)->name

        - 间接成员运算符 ->
    - new 运算符依据类型确定所需内存字节数，找到内存后返回其地址
    - delete释放内存

      - delete pt;
      - delete [] pt;
      - delete释放的是指针所指向的地址处被new分配的内存，而非指针
  - const和指针

    - 指向const对象的指针 const int \* pt;

      - | 声明 | 指针 | 变量 | 直接改变变量 | 通过指针改变变量 |
        | --- | --- | --- | --- | --- |
        | int value; int \* pt = &value; | 常规 | 常规 | ✅ | ✅ |
        | int value; const int \* pt = &value; | const | 常规 | ✅ | ❎ |
        | const int value; const int \* pt = &value; | const | const | ❎ | ❎ |
        | const int value; int \* pt = &value; | 常规 | const | INVALID | INVALID |
    - const指针 int \* const pt;

      - 无法修改pt的指向
- 循环

  - for循环

    - for (initialization; test-expression; update-expression) body

      - 运行顺序

        - 1.设置初始值

          - c++可以在for循环的初始化部分中声明变量，且变量只存在于for循环中，当离开循环变量消失
        - 2.执行测试
        - 3.执行循环操作
        - 4.更新用于测试的值
    - 复合语句（语句块）

      - {statement} 被视为一条语句
      - 在语句块中定义的新的变量，仅当程序执行该语句块中的语句时，该变量才存在。执行完该语句块后，变量将被释放。
    - 逗号运算符

      - 将两个表达式放到只允许放一个表达式的地方
      - eg: ++j, --i
    - 表达式省略

      - 只有两个分号是必须的
      - 测试表达式被省略则测试结果为true
  - while循环

    - while (test-condition) body
  - do while 循环

    - do body while (test-ecpression);
  - break 语句

    - 运用在switch语句和循环中
    - 跳到switch或循环后面
  - continue 语句

    - 运用在循环中
    - 跳过循环体中余下的代码，开始新一轮循环
- 分支

  - if 语句

    - if (test-condition) statement
  - if else 语句

    - if (test-condition) statement1 else statement2

      - if-else算作一条语句
      - - ![](https://api2.mubu.com/v3/document_image/69f7b8f3-72fa-4132-9d37-cd05fbff27b6.jpeg)
    - if else if else 结构
  - switch 语句

    - switch (integer-expression) {case label1 : statements case label2 : statements2 default : statements}
    - integer-expression是结果为整数的表达式，标签是整数常量

      - 标签：int/char/枚举量/...
    - 程序跳到switch中特定代码行后，将依次执行之后的所有语句
  - goto语句

    - goto lablel;
    - label: statement
- 表达式

  - 算数表达式

    - 单目：+ -（正负） ++ --
    - 双目：+ - \* / %
    - 优先级（由高到低）

      - 单目 + - ++ --
      - 双目 \* / %
      - 双目 + -
  - 赋值表达式

    - 将右侧值赋给左侧值
    - 其值定义为左侧成员的值
    - 结合性从右至左
  - 关系表达式

    - 运用关系运算符
    - 比较结果为真，则其值为true（1），否则为false（0)
  - 逻辑表达式

    - 由逻辑运算符将两个表达式连接
    - 结果 true（1）或 false（0）
    - 左结合
  - 条件表达式
  - 逗号表达式
- 运算符

  - 算数运算符 + - \* / %

    - 除法分支

      - 整型 / 整型 = 整数（小数部分直接删除）
      - 整数 / 浮点数 = 浮点数 （有一个浮点数就保留小数）
    - 整型 % 整形 = 余数
  - 赋值运算符 =

    - 右值 赋给 左值
  - 关系运算符

    - - ![](https://api2.mubu.com/v3/document_image/1970090_06583004-5318-4491-8ca2-cc84fe66548c.png)
  - 逻辑运算符

    - && AND和

      - 从左到右判断，若第一个为假则停止判断
    - || OR或

      - 从左到右判断，若第一个为真则停止判断
    - ！NOT否
    - AND优先级高于OR
  - 条件运算符 ?:

    - expression1 ? expression2 : expression3
    - 如果expression1为true，则表达式的值为expression2的值
    - 如果expression1为false，则表达式的值为expression3的值
  - sizeof运算符

    - sizeof ( 类型名 ）
    - sizeof 变量
    - sizeof ( 变量 )
    - sizeof(数组名）

      - 返回整个数组的大小
    - sizeof（指针）

      - 返回指针变量的长度
    - sizeof 是运算符 文件自带 不用前缀
  - 递增运算符（++）和递减运算符（--）

    - a++：使用a的当前值计算表达式，然后将a的值加1
    - ++a：先将a的值加1，然后使用新的值来计算表达式
    - 递增递减运算符和指针

      - 前缀递增、前缀递减和解除引用运算符的优先级相同，以从右到左的方式进行结合。
      - 后缀递增和后缀递减的优先级相同，但比前缀运算符的优先级高，这两个运算符以从左到右的方式进行结合。
      - 总的来说从右到左
  - 组合赋值运算符

    - - ![](https://api2.mubu.com/v3/document_image/1970090_d9d03746-5405-4033-bf36-37e6d6ae0997.png)
- 无法改变指向的值得指针，const int \*pt
- 无法改变代表的值的引用，const int & name = ？
- 无法改变所指的指针，int \* const pt
- 指针数组 int \* pt[4]