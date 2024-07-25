cmake_minimum_required(VERSION 3.0)

project(grid_probability_test)

set(CMAKE_BUILD_TYPE Debug)
# 添加调试信息
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g")

# 设置 C++ 标准为 C++14
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

file(GLOB_RECURSE CORE_SRC "*.cc")

# 寻找 OpenCV 包
# find_package(OpenCV REQUIRED)

find_package(Eigen3 REQUIRED)
find_package(Boost REQUIRED)
# find_package(glog REQUIRED)

# 包含 OpenCV 头文件目录
# include_directories(${OpenCV_INCLUDE_DIRS})

include_directories(${Boost_INCLUDE_DIRS})
include_directories(${EIGEN3_INCLUDE_DIRS})


add_executable(grid_probability_test main.cpp ${CORE_SRC})
# 链接 OpenCV 库
target_link_libraries(grid_probability_test Eigen3::Eigen ${Boost_LIBRARIES})

install(TARGETS grid_probability_test RUNTIME DESTINATION bin)
