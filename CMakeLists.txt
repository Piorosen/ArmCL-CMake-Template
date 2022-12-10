cmake_minimum_required(VERSION 3.10)
SET(PROJECT_NAME template_armcl)
project(template_armcl)

SET (CMAKE_C_COMPILER "g++")
set(CMAKE_CXX_STANDARD 14)

message(${CMAKE_SOURCE_DIR})
MESSAGE(${CMAKE_BINARY_DIR})

link_directories(${CMAKE_SOURCE_DIR}/external)
include_directories(base include)

add_executable(${PROJECT_NAME} main.cpp
        tuner/tuner.cpp
        tuner/genetic_algorithm.cpp
        tuner/all_search.cpp
        tuner/grid_search.cpp
        tuner/random_search.cpp
        tuner/strategy_factory.cpp
        base/utils/Utils.cpp 
        base/utils/GraphUtils.cpp 
        base/utils/CommonGraphOptions.cpp
)

target_link_libraries(${PROJECT_NAME} arm_compute_core
        arm_compute_graph
        arm_compute
        )

target_include_directories(${PROJECT_NAME} PUBLIC
        base
        include)
