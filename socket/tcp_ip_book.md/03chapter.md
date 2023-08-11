ipv4:4字节；ipv6：16字节

目前主流ipv4，ipv6防止用尽

交换机/路由器：内外网数据交换
***
端口号就是在同一操作系统内为区分不同套接字而设置的，因此无法将1个端口号分配给不同套接字。

另外，端口号由16位构成，可分配的端口号范围是0-65535。但0-1023是知名端口( Well-known PORT )，一般分配给特定应用程序，所以应当分配此范围之外的值。

另外，虽然端口号不能重复，但TCP套接字和UDP套接字不会共用端口号，所以允许重复。例如:如果某TCP套接字使用9190号端口，则其他TCP套接字就无法使用该端口号，但UDP套接字可以使用。

总之，数据传输目标地址同时包含IP地址和端口号，只有这样，数据才会被传输到最终的目的应用程序（应用程序套接字)。
***
表示IPv4地址的结构体
```
struct sockaddr_in{
    sa_family_t     sin_family;           //地址族（Address Family )
    uint16_t    sin_port;       //16位TCP/UDP端口号
    struct in_addr  sin_addr;       //32位IP地址
    char    sin_zero[8];      //不使用,为了和sockaddr(bind参数)保持大小一致
}
```
思考:sockaddr_in表示ipv4地址的结构体，为什么还需要声明不同ip地址块的地址族？

答：sockaddr并不只是为ipv4设计
***
#字节序

不同CPU中，4字节整数型值1在内存空间的保存方式是不同的。4字节整数型值1可用2进制表示如下

00000000 00000000 00000000 00000001

有些CPU以这种顺序保存到内存，另外一些CPU则以倒序保存。

00000001 00000000 00000000 00000000

CPU向内存保存数据的方式有2种，这意味着CPU解析数据的方式也分为2种。

大端序（ Big Endian ):高位字节存放到低位地址。

小端序( Little Endian):高位字节存放到高位地址。

网络传输统一为大端序

字节序转换函数
```
htons;  ntohs;  htonl;  ntohl;
h:host  n:net   l:long  s:short  
```
***
```
inet_addr():将字符串形式的点十分的ip地址转化为32位整数，如果无效地址，返回检测值

但一般都使用inet_aton (internet:address to network);
可以直接将转换后的ip地址赋值给sockaddr_in结构体

inet_ntoa:反向解析
```
***
#网络地址初始化
```
structsockaddr_in addr;
char * serv_ip = "211.217.168.13";  //声明IP地址字符串
char * serv_port - "9190";  //声明端口号字符串
memset( &addr，e，sizeof(addr));    //结构体变量addr的所有成员初始化为0
//这个操作主要为了把sin_zero置0；

addr.sin_family = AF_INET;  //指定地址族
addr.sin_addr.s_addr = inet_addr(serv_ip);  //基于字符串的IP地址初始化
/*
当频繁socket连接，服务端需要回应不同的ip地址，
可以把serv_ip换成INADDR_ANY，表示接收任何ip地址绑定
*/

addr.sin_port = htons(atoi( serv_port));  //基于字符串的端口号初始化
```
***
创建服务器端套接字需要ip地原因：

一台计算机有多个ip地址：多个nic：network interface card

```
向套接字分配地址的bind函数原型如下:
int bind(int sockfd，struct sockaddr *myaddr，socklen_t addrlen);

而调用时则用
bind(serv_sock，(struct sockaddr *) &serv_addr，sizeof(serv_addr));

此处serv_addr为sockaddr_in结构体变量。
与函数原型不同，传入的是sockaddr_in结构体变量，请说明原因。
```
答：在C语言中，存在结构体的类型兼容性（type compatibility）规则。

这意味着如果一个函数接受的参数是某种类型的指针，而传递给该函数的实际参数是指向另一种兼容类型的指针，那么编译器会认为这是合法的。

sockaddr_in 是一个用于表示网络地址的更具体的结构体，而 struct sockaddr 是一个通用的网络地址结构体




