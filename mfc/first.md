software development kit
Windows应用程序API函数是通过C语言实现的,所有主要的 Windows函数都在Windows.h头文件中进行了声明。一千多个api
一个程序至少一个窗口   父子窗口
在Windows应用程序中,窗口是通过窗口句柄HWND来标识的。句柄：handle 资源标识号

当Windows操作系统启动一个程序时,它调用的就是该程序的WinMain函数：实际是插入到可执行文件中的启动代码调用的。
底层文件名：windows.c
右键转到声明        __stdcall表示参数从右向左压入堆栈
instance 实例
int WINAPIWinMain{
    HINSTANCE hinstance  //应用程序实例
    HINSTANCE hPrevinstance,   //上个应用程序实例
    LPSTR lpCmdline  //命令行参数
    int nShowCmd；   //窗口显示的样式

WNDCLASS wc  创建窗口类
hbrBackground color_brush 背景颜色    hCursor 设置光标  hIcon 图标
vs里按F1 进入文档   lpfnWndProc 

应用程序类型：基于对话框  rc dialog  视图，工具箱    dlg.h 里去设置变量    DDX_TEXT
UpdateData(TRUE) == 将控件的值赋值给成员变量;UpdateData(FALSE) == 将成员变量的值赋值给控件
TRUE:窗口值给变量
Dialog（对话框）  rc则可以打开资源视图   .h定义文件   .cpp实现文件

新建窗口：1、新建dialog 2、添加类 3、dlg.h里实例化类(记得包含头文件)
双击button，转入dlg.cpp  写一个domodal DoModal是一个函数，可以用来显示一个模态对话框。此成员函数用来显示一个模态对话框
界面打开：资源视图：dialog 

模态是人机交互过程中的一种状态,表现为用户相同的操作在模态下可以产生不同的结果
oninitdialog:初始化

CString常用于MFC编程中，是属于MFC的类，如从对话框中利用GetWindowText得到的字符串就是CString类型
Static Text是一个文本显示控件，用于显示文字

打开filechoose类：创建一个shelltree shelllist 然后各自添加变量控件   shelllist里添加事件处理（鼠标点击）
为文件路径编辑框新建一个变量值mystr

MessageBox(_T("内容"), _T("标题"), 按钮组合参数);  弹窗函数

非模态(Modeless)对话框，又叫做无模式对话框，当用户打开非模态对话框时，依然可以操作其他窗口
非模态对话框实现方式不一样，先创建(CDialog::Create)一次，然后再显示(CWnd::ShowWindow)。
//启动非模拟对话框按钮
void CMFC01Dlg::OnBnClickedButton2()
{
 //需要在MEC01Dlg.cpp开头包含头文件 #include "DlgShow.h"
 //弹出非模态对话框
 CDlgShow dlg;
 //创建
 dlg.Create(IDD_DIALOG_SHOW);
 //显示
 dlg.ShowWindow(SW_SHOWNORMAL);
}

所有静态文本框的缺省ID都是IDC_STATIC，静态ID，不响应任何消息（事件）
CString既可以处理Unicode标准的字符串，也可以处理ANSI标准的字符串

窗口的名字：属性：描述文字
