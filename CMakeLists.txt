cmake_minimum_required(VERSION 3.31)
project(cprimerplus_6th_code C)

set(CMAKE_C_STANDARD 11)

add_executable(cprimerplus_6th_code main.c)

######### 这一组代码是实现 exe 文件统一放在 bin 文件夹下的 ###################
################## 每次更新文件夹后，需要reload ##########################
# 设置可执行文件的统一输出目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# 递归查找所有 .c 文件（包括子文件夹）
file(GLOB_RECURSE SRC_FILES "${CMAKE_SOURCE_DIR}/*.c")

# 为每个 .c 文件生成对应的可执行文件
foreach(src_file ${SRC_FILES})
    # 获取文件名（不带路径和扩展名）作为可执行文件名
    get_filename_component(exe_name ${src_file} NAME_WE)

    # 添加可执行文件
    add_executable(${exe_name} ${src_file})
endforeach()
########################################################################