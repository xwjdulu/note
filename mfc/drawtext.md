单文档就是一个窗口只能处理一个文档，多文档就是同时可以处理多个，共享工具栏，菜单栏什么的，
对话框就是一个提示用户进行选择或者确认的窗体。
对话框模板适合于做交互界面，单文档模板适合于做文件处理，多文档模板适合于做多文件处理。

CxxxxView  视窗类 所有的按键 等消息都先在这里响应
CxxxxDoc   文档类
CMainFrame 框架类
CxxxxApp   应用程序类

和教程名字不同，注意是否变量前有项目名