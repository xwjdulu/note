int mysql_query(MYSQL *mysql, const char *query)
参数介绍:mysql 连接句柄    query 执行的sql
反回值：成功 返回 0    失败 返回 非0

MYSQL m_sqlCon;   声明数据库对象
mysql_init(&m_sqlCon)的作用是初始化一个数据库对象，我们下面的所有操作都是针对这个对象而进行的。
mysql_set_character_set(&m_sqlCon, "gb2312")，没有这行代码，你的窗口提示等组件中的内容就会出现中文乱码现象。
mysql_real_connect(&m_sqlCon, 地址, 用户名, 密码, 数据库,端口, NULL, 0) 

mysql_free_result(res); //释放一个结果集合使用的内存。
mysql_close(&mysql); //关闭一个服务器连接。
