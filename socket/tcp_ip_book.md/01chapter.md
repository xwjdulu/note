有的服务器不是ip地址是dns，需要写一个解析函数

accept再创建一个socket对象给其收发消息。原因是现实中服务端都是面对多个客户端，那么为了区分各个客户端，则每个客户端都需再分配一个socket对象进行收发消息
***
#socket各函数返回值

```
#include <sys/socket.h>

int socket(int domain, int type, int protocol);
相当于电话机
成功时返回文件描述符，失败时返回-1。

int bind(int sockfd , str‘uct sockaddr *myaddr, socklen addrlen);
成功时返回0，失败时返回-1。
分配端口

int listen(int sockfd , int backlog);
成功时返回0，失败时返回-1。
相当于保持可请求的连接状态

int accept(int sockfd, struct sockaddr *addr... socklen_t *addrlen);
成功时返回文件描述符，失败时返回-1
接收请求
```
***
#各文件函数
```
#include <unistd.h>

int open(const char *path int flag);
成功时返回文件描述符，失败时返回-1。

int close(int fd);
成功时返回日，失败时返回-1。

ssize_t write(int fd, const void *buf，size_t nbytes);
成功时返回写入的字节数，失败时返回-1。

ssize_t read(int fd, void * buf， size_t nbytes);
→成功时返回接收的字节数〔但遇到文件结尾则返回日)，失败时返回-1。
```
***
windows下coscket
```
#include <winsock2.h>

int WSAStartup(wORD wVersionRequested，LPWSADATA 1pwSAData);
→成功时返回0，失败时返回非零的错误代码值。

int WSACleanup(void);
成功时返回0，失败时返回SOCKET_ERROR。
```
***
Linux中，对套接字数据进行IO时可以直接使用文件IO相关函数;而在Windows中则不可以。原因为何?

在 Linux 中，套接字也被视为文件。换句话说，这两者被设计成不加区分的形式。因此，可以将文件 I/O 函数用于套接字的 I/O。但是，Windows 与 Linux 不同，它不会将套接字与文件等同看待。因此，文件 I/O 函数和套接字 I/O 函数在 Windows 中是分开的。

Linux中的文件描述符与Windows的句柄实际上非常类似。请以套接字为对象说明它们的含义。

Linux 的文件描述符是为了区分和指代文件而分配的整数值。同样地，Windows 的句柄是为了区分和指代套接字而分配的整数值。

底层文件IO函数与ANSI标准定义的文件I/O函数之间有何区别?

ANSI 标准定义的输入输出函数是 C 标准提供的，无论操作系统如何，都可以调用这些函数。另一方面，底层文件 I/O 函数是操作系统提供的输入输出函数。因此，它们是操作系统特定的，不同操作系统可能具有不同形式的底层文件 I/O 函数。
