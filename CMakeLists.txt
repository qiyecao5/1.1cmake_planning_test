cmake_minimum_required(VERSION 3.29.0) # 这个就是设置你cmake所需要的最小版本
project(planning)  # 就是你这个项目的名字
set(CMAKE_CXX_STANDARD 17) # 指定C++的标准 这里选择的17标准

# 变量和目录设置
# 把动态库和exe都指定到bin目录下面
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
# 上面的这个命令只适合windows平台
# linxu平台 就需要CMAKE_LIBRARY_OUTPUT_DIRECTORY
# 静态库就是用这个了CMAKE_ARCHIVE_OUTPUT_DIRECTORY,静态库只会把bin制定出来,而可执行文件 并不会管它

# 动态库
# 抓取src下面的所有的.cpp文件
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
# 我们要先生成一个动态库
# 给动态库取个名字教 common
# 这也就是说,把src目录下的所有.cpp文件 生成一个动态库
add_library(common
SHARED
${SRC_LISTS}
)

# 因为上面的动态库 要依赖include文件里面的头文件,所以还要包含以下头文件的目录
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# 可执行文件
# 生成可执行文件 (planning_main.cpp就是程序入口,就用它来生成就可以)
add_executable(planning_main planning_main.cpp)
# 我们要让上面生成的这个可执行文件planning_main,去包含上面那两个头文件目录

# 同样 planning_main这个可执行文件 也要包含 这个库
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

# 链接
# 最后把这个可执行文件 链接到 生成的这个动态库上面
target_link_libraries(planning_main 
PUBLIC
common
)