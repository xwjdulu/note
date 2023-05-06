列表视图控件List Control同样比较常见，它能够把任何字符串内容以列表的方式显示出来

1）CString类型不能自动装换为const char*。
2）const char*类型可自动装换为CString。
3）std::string类型调用c_str()方法就可轻松转换为const char*。
4）CString与std::string相互转换

LPCTSTR用来表示你的字符是否使用UNICODE, 如果你的程序定义了UNICODE或者其他相关的宏，那么这个字符或者字符串将被作为UNICODE字符串，否则就是标准的ANSI字符串。

T2A的用法：CString ==> char*