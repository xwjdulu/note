CMFCShellListCtrl::DisplayFolder	显示包含在提供的文件夹中的项列表
CMFCShellListCtrl::GetItemPath	返回项的文本路径

当关联的数据是Value（数值型）数据时：
使用UpdateData(TRUE)    将从获取控件值------>该值自动更新到关联变量中 【编辑器输入值-> cpp中实际对应的关联变m_edit中】
使用UpdateData(FALSE)   将更新控件值------>关联变量的值更新到界面中
注:UpdateData()默认为True。

当关联数据为控件型（Control类型）：
Control是一个控件，可以使用该控件的所有方法。
如假设关联变量为m_CEdit.则可以使用m_CEdit.GetWindowTextW(变量名)，将空间内容赋值到变量中
使用m_CEdit.SetWindowTextW(变量名)，将变量值更新到控件上。

