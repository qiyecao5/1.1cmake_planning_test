# 1.1cmake_planning_test
这5个文件全都放在一个目录下面. 这样的话,我们只需要一个CMakeLists.txt  就可以管理我们整个项目了, 适合非常小型的项目
模拟一个planning项目
假设使用到两个模块
pnc_map 规划模块对于地图的处理
每个模块又分为 .h  和 .cpp
process	规划的主过程
每个模块又分为 .h  和 .cpp
main	这个模块的入口函数
.cpp
这个项目一共就这5个文件
