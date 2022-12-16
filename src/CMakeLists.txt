cmake_minimum_required(VERSION 3.21.3)  # cmake minimum version
#set(FBXSDK_NAME milesFBX)
set(FBXSDK_LIB "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/lib/vs2019/x64/debug")
set(FBXSDK_INCLUDE "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/include")
set(CMAKE_PREFIX_PATH ${FBXSDK_LIB})
#add_library(milesFBX SHARED
#        ${FBXSDK_ROOT}/libfbxsdk.dll
#)
#set_target_properties(milesFBX PROPERTIES LINKER_LANGUAGE CXX)

#set(MILESLIB_NAME milesLIB)
add_library(milesLIB
    see.cpp
)

#add_library(mha SHARED IMPORTED)
#set_target_properties(mha PROPERTIES IMPORTED_LOCATION ${FBXSDK_ROOT}/libfbxsdk.dll)

find_library(FBXSDK fbxsdk)

message(fbxsdk: ${FBXSDK})

#message(CMAKE_PREFIX_PATH ${CMAKE_PREFIX_PATH})

target_include_directories(milesLIB
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
        ${FBXSDK_INCLUDE}
)


