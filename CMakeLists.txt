cmake_minimum_required(VERSION 3.12) ## 支持的cmake最低版本

project(STM32 C CXX ASM) # 项目名称, 支持的编程语言
message(STATUS "Building project: ${PROJECT_NAME}")

# STM32_PROJ_FOLDER 存储的是 src 目录下 stm32proj 文件夹, 相当于 stm32 项目的根目录
set(STM32_PROJ_FOLDER stm32proj)
set(PROJECT_ROOT_DIR "${CMAKE_SOURCE_DIR}")
message(STATUS "Project root directory: ${PROJECT_ROOT_DIR}")

# 默认构建类型是 Debug, 可以通过 cmake .. -DCMAKE_BUILD_TYPE=Release, 将构建类型切换成 Release
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Debug)
endif(NOT CMAKE_BUILD_TYPE)

if(CMAKE_BUILD_TYPE MATCHES Debug)
    message(STATUS "Build type: Debug")
elseif(CMAKE_BUILD_TYPE MATCHES Release)
    message(STATUS "Build type: Release")
endif()

# 添加一个子目录
add_subdirectory(src)
