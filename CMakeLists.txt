cmake_minimum_required(VERSION 3.21.3)

project(fbx-tools VERSION 0.1.0)

#include(CTest)
#enable_testing()

set(FBXSDK_LIB "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/lib/vs2019/x64/debug")
set(FBXSDK_INCLUDE "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/include")
set(PROJECT_INCLUDE "${PROJECT_SOURCE_DIR}/include")
set(EXE_NAME fbx-tools)

add_subdirectory(src)

add_executable(${EXE_NAME} main.cpp)

target_include_directories(${EXE_NAME}
    PUBLIC
        ${PROJECT_INCLUDE}
)

target_link_libraries(${EXE_NAME}
    PUBLIC
        milescore
        #${FBXSDK_LIB}/libfbxsdk.lib
)

target_compile_features(${EXE_NAME}
    PUBLIC
        cxx_std_17
)

# 这段代码能够将 milesCore 这个库的编译后的目标文件( libmilescore.dll )拷贝到 ${EXE_NAME} 的目标文件目录下
add_custom_command(TARGET ${EXE_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_if_different
        $<TARGET_FILE:milescore>
        $<TARGET_FILE_DIR:${EXE_NAME}>
)


set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
#include(CPack)

