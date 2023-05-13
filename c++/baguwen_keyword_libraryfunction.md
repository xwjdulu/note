sizeof 和 strlen 的区别
strlen 是头文件 中的库函数，sizeof 是 C++ 中的运算符。
strlen 测量的是字符串的实际长度，以 \0 结束。而 sizeof 测量的是字符数组的分配大小。
strlen 本身是库函数，因此在程序运行过程中，计算长度；而 sizeof 在编译时，计算长度；
sizeof 的参数可以是类型，也可以是变量；strlen 的参数必须是 char* 类型的变量
若字符数组 arr 作为函数的形参，sizeof(arr) 中 arr 被当作字符指针来处理，strlen(arr) 中 arr 依然是字符数组

explicit 的作用
用来声明类构造函数是显示调用的，而非隐式调用，可以阻止调用构造函数时进行隐式转换。只可用于修饰单参构造函数!!!
因为无参构造函数和多参构造函数本身就是显示调用的

static 的作用
static 作用于局部变量，改变了局部变量的生存周期，使得该变量存在于定义后直到程序运行结束的这段时间。
static 作用于类的成员变量和类的成员函数，使得类变量或者类成员函数和类有关，
也就是说可以不定义类的对象就可以通过类访问这些静态成员
static 作用于全局变量和函数，改变了全局变量和函数的作用域，使得全局变量和函数只能在定义它的文件中使用

static 在类中使用的注意事项
静态成员变量是在类内进行声明，在类外进行定义和初始化
静态成员变量相当于类域中的全局变量，被类的所有对象所共享，包括派生类的对象
静态成员变量可以作为成员函数的参数，而普通成员变量不可以。
静态数据成员的类型可以是所属类的类型，而普通数据成员的类型只能是该类类型的指针或引用。
静态成员函数不能调用非静态成员变量或者非静态成员函数，因为静态成员函数没有 this 指针。静态成员函数做为类作用域的全局函数。
静态成员函数不能声明成虚函数（virtual）const 函数和volatile 函数(用它声明的类型变量表示可以被某些编译器未知的因素更改)

static 全局变量和普通全局变量的异同
普通全局变量和 static 全局变量都是静态存储方式
普通全局变量的作用域是整个源程序，当一个源程序由多个源文件组成时，普通全局变量在各个源文件中都是有效的；
静态全局变量则限制了其作用域，即只在定义该变量的源文件内有效，在同一源程序的其它源文件中不能使用它。由于静态全局变量的作用域限于一个源文件内，只能为该源文件内的函数公用，因此可以避免在其他源文件中引起错误。
静态全局变量只初始化一次，防止在其他文件中使用

 const 作用及用法
 const 修饰成员变量，定义成 const 常量，相较于宏常量，可进行类型检查，节省内存空间，提高了效率
 使用#define 定义宏常量的时候，一般的情况下不能在后加分号； #define pi 3.14  又在内部给该常量进行赋值，其不可改变   
const 修饰函数参数，使得传递过来的函数参数的值不能改变。
const 修饰成员函数，使得成员函数不能修改任何类型的成员变量（mutable 修饰的变量除外），也不能调用非 const 成员函数，
而实际开发过程中，我们可能需要对某些成员变量进行修改，就需要用到 mutable
因为非 const 成员函数可能会修改成员变量。
因此不能在类的声明中初始化 const 成员变量，类的对象还没有创建，编译器不知道他的值。

define与const的区别
1.define作用在预处理时，是简单地字符替换
2. const作用在编译时，具有类型检查的功能
3. const必须进行初始化
define 是在编译预处理阶段进行替换，const 是在编译阶段确定其值。
安全性：define 定义的宏常量没有数据类型，只是进行简单的替换，不会进行类型安全的检查；const 定义的常量是有类型的，是要进行判断的，可以避免一些低级的错误。
内存占用：define 定义的宏常量，在程序中使用多少次就会进行多少次替换，内存中有多个备份，占用的是代码段的空间；const 定义的常量占用静态存储区的空间，程序运行过程中只有一份。
调试：define 定义的宏常量不能调试，因为在预编译阶段就已经进行替换了；const 定义的常量可以进行调试。

define 和 typedef 的区别
#define 作为预处理指令，在编译预处理时进行替换操作，不作正确性检查，只有在编译已被展开的源程序时才会发现可能的错误并报错
typedef 是关键字，在编译时处理，有类型检查功能，用来给一个已经存在的类型一个别名，但不能在一个函数定义里面使用 
typedef 用来定义类型的别名，方便使用。
#define 不仅可以为类型取别名，还可以定义常量、变量、编译开关等。
#define 没有作用域的限制，只要是之前预定义过的宏，在以后的程序中都可以使用，而 typedef 有自己的作用域。
指针的操作：typedef 和 #define 在处理指针时不完全一样

trcpy 函数和memcpy 函数
void *memcpy(void *destin, void *source, unsigned n);
strcpy函数：提供了字符串的复制。即strcpy只用于字符串复制，并且它不仅复制字符串内容之外，还会复制字符串的结束符'\0'。
memcpy函数：提供了一般内存的复制。可以复制其他任意数据类型。

new/delete和malloc/free的区别
new/delete是C++的关键字;malloc/free是C/C++的库函数，需要stdlib.h；
都可用于申请动态内存和释放内存，new/delete在对象创建的时候自动执行构造函数，对象消亡前自动执行析构函数，底层实现其实也是malloc/free
new无需指定内存块的大小，编译器会根据类型信息自行计算；malloc需要显式地支持所需内存的大小
new返回指定类型的指针，无需进行类型转换；malloc默认返回类型为void*，必须强行转换为实际类型的指针
new内存分配失败时会抛出bad_alloc异常；malloc失败时返回NULL

inline函数
被频繁调用的函数会导致栈空间或栈内存的大量消耗，因此引入inline修饰函数，即内联函数；内联函数将在程序的每个调用点上“内联式地”展开。内联以代码膨胀为代价，省去了函数调用的开销，从而提高函数的执行效率
inline定义的类的内联函数，函数的代码被放入符号表中，在使用时直接进行替换（像宏一样展开），没有了调用的开销，效率也很高。

volatile，可以和 const 同时使用吗
volatile 限定符是用来告诉计算机，所修饰的变量的值随时都会进行修改的。用于防止编译器对该代码进行优化。通俗的讲就是编译器在用到这个变量时必须每次都小心地从内存中重新读取这个变量的值，而不是使用保存在寄存器里的备份。 const 和 volatile 可以一起使用，volatile 的含义是防止编译器对该代码进行优化，这个值可能变掉的。而 const 的含义是在代码中不能对该变量进行修改


