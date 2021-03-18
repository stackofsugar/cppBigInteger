cmake_minimum_required(VERSION 3.18.0)

project(cppBigInteger)

set (srcfiles_raw

)

set(srcfiles "")
foreach(target_srcfile IN LISTS srcfiles_raw)
    set(srcfiles ${srcfiles} "${CMAKE_CURRENT_SOURCE_DIR/src/${target_srcfile}.cpp}")
endforeach(target_srcfile IN LISTS srcfiles_raw)

set (libfiles_raw

)

set(libfiles "")
foreach(target_libfile IN LISTS libfiles_raw)
    set(libfiles ${libfiles} "${CMAKE_CURRENT_SOURCE_DIR/src/${target_libfile}.h}")
endforeach(target_libfile IN LISTS libfiles_raw)

add_library(BigIntegerLib STATIC ${libfiles})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall")

# Testing using static lib
add_executable(${PROJECT_NAME} test.cpp)
target_include_directories(${PROJECT_NAME} PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_link_libraries(${PROJECT_NAME} BigIntegerLib)