cmake_minimum_required(VERSION 2.5)
project(mymuduo)

# cmake => makefile   make
# mymuduo最终编译成so动态库，设置动态库的路径，放在根目录的lib文件夹下面
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
# 设置调试信息 以及 启动C++11语言标准
# -fPIC（-fpic）
# -fPIC 作用于编译阶段，告诉编译器产生与位置无关代码(Position-Independent Code)，则产生的代码中，
# 没有绝对地址，全部使用相对地址（相对寻址指令，或通过巧妙的计算等到相对位置），故而代码可以被加载到内存的任意位置，被所有需要的进程共享，并都可以正确执行。
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11 -fPIC")

# 定义参与编译的源代码文件 
aux_source_directory(. SRC_LIST)
# 编译生成动态库mymuduo
add_library(mymuduo SHARED ${SRC_LIST})