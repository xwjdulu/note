代码能正常运行，出现波浪线：
1，ctrl + shift + p, 然后输入 >C/C++  ，选择 编辑配置(JSON)

2，终端输入 gcc -v -E -x c++ -

3，#include <...> search starts here:之后的路径加到json文件的includepath中，
注意要在后面加 /**，导入该文件下所有包的意思
***

