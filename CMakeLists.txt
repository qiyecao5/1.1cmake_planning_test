cmake_minimum_required(VERSION 3.29.0) # 这个就是设置你cmake所需要的最小版本
project(planning)  # 就是你这个项目的名字
set(CMAKE_CXX_STANDARD 17) # 指定C++的标准 这里选择的17标准

# /bin 创建一个bin目录 用来存放 我们的exe可执行文件
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

# .就是当前文件  获取所有.cpp文件  都打包到SRC_LIST这个变量中, 
aux_source_directory(. SRC_LIST)

# 生成可执行文件
# planning_main参数是 可执行文件的名称
# SRC_LIST参数代码的变量,代表程序是由它生成的
add_executable(planning_main ${SRC_LIST})
