cmake_minimum_required(VERSION 2.8)
project(g2o_curve_fitting)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++11 -O3")

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake_modules)

# Find G2O
find_package(G2O REQUIRED)
include_directories(
    ${G2O_INCLUDE_DIRS}
    "/usr/include/eigen3"
)

# OpenCV
find_package(OpenCV REQUIRED)
include_directories(${OpenCV_DIRS})

add_executable(curve_fitting main.cpp)
# Link with G2O and OpenCV
target_link_libraries(curve_fitting
    ${OpenCV_LIBS}
    g2o_core g2o_stuff
)
