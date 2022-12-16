cmake_minimum_required(VERSION 3.21.3)

project(fbx-tools VERSION 0.1.0)

include(CTest)
enable_testing()

set(FBXSDK_LIB "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/lib/vs2019/x64/debug")
set(FBXSDK_INCLUDE "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/include")
set(PROJECT_INCLUDE "${PROJECT_SOURCE_DIR}/include")
set(CMAKE_PREFIX_PATH ${FBXSDK_LIB})

find_library(FBXSDK fbxsdk-mt)
message(fbxsdk: ${FBXSDK})

add_subdirectory(src)

set(EXE_NAME fbx-tools)

add_executable(${EXE_NAME} main.cpp)

target_include_directories(${EXE_NAME}
    PUBLIC
        ${PROJECT_INCLUDE}
)

target_link_libraries(${EXE_NAME}
    PUBLIC
        milesLIB
)

target_compile_features(${EXE_NAME}
    PUBLIC
        cxx_std_17
)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
