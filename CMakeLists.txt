cmake_minimum_required(VERSION 3.21.3)
project(fbx-tools VERSION 0.1.0)

include(CTest)
enable_testing()

add_subdirectory(src)

set(EXE_NAME fbx-tools)

add_executable(${EXE_NAME} main.cpp)

target_include_directories(${EXE_NAME}
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
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
