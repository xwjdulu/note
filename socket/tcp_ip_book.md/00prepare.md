extern声明外部变量，使得这个变量在当前文件中可用，该变量是在别的文件中定义的

作用：在头文件中extern，使得头文件每次被引入不会重复声明
***
shift+右键，输入start cmd：Windows下文件夹启用cmd

#socket流程

客户端：1：创建socket()；2：connect();3:send()/receive();4:close();

服务端:1:socket();2:bind();3:listen();4:accept();5:recive()/send();close();

本地地址：127.0.0.1

对于linux，socket被认为是文件，socket操作和文件操作没有区别

file descriptor: 即windows的句柄
```
0:输入；   1：输出；  2：错误；
```

