cmake_minimum_required (VERSION 2.6)
project (hnsw_lib)

include_directories("${PROJECT_BINARY_DIR}")



set(SOURCE_EXE main.cpp)            

set(SOURCE_LIB sift_test.cpp)

add_library(sift_test STATIC ${SOURCE_LIB})


add_executable(main ${SOURCE_EXE})
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp -fno-rtti -Wall")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -g -fsanitize=address -static-libasan")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -g -flto -ftree-vectorize -march=native -Ofast -lrt -DNDEBUG -DHAVE_CXX0X -fpic -w -ftree-vectorizer-verbose=0")

target_link_libraries(main sift_test)
