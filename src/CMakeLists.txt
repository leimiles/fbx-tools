cmake_minimum_required(VERSION 3.21.3)  # cmake minimum version

set(FBXSDK_NAME milesFBX)
set(FBXSDK_ROOT "C:/Program Files/Autodesk/FBX/FBX SDK/2020.3.2/lib/vs2019/x64/debug")
add_library(${FBXSDK_NAME} SHARED
        ${FBXSDK_ROOT}/libfbxsdk.dll
)

set_target_properties(${FBXSDK_NAME} PROPERTIES LINKER_LANGUAGE CXX)

set(MILESLIB_NAME milesLIB)
add_library(${MILESLIB_NAME}
    see.cpp
)

target_link_libraries(${MILESLIB_NAME}
    PUBLIC
        ${FBXSDK_NAME}
)

target_include_directories(${MILESLIB_NAME}
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)
