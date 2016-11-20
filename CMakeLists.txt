cmake_minimum_required(VERSION 3.0)
project(typus CXX)


set(GTEST_DIRECTORY vendor/googletest/googletest)


add_library(googletest STATIC
           ${GTEST_DIRECTORY}/src/gtest-all.cc
           ${GTEST_DIRECTORY}/src/gtest_main.cc)

target_include_directories(googletest 
                           PUBLIC  ${GTEST_DIRECTORY}/include 
                           PRIVATE ${GTEST_DIRECTORY})
add_executable(all-tests
               tests/result.cc)
target_include_directories(all-tests 
                           PRIVATE include)

set_property(TARGET all-tests PROPERTY CXX_STANDARD 11)
target_link_libraries(all-tests googletest)
