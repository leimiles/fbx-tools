cmake_minimum_required(VERSION 3.21.3)  # cmake minimum version

add_library(milescore
    SHARED
        see.cpp
)

target_include_directories(milescore
    PUBLIC
        ${PROJECT_INCLUDE}
        ${FBXSDK_INCLUDE}   # 只有写在这里才能被这个编译库找到
)



