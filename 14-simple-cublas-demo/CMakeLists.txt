CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(simple-cublas-demo CXX CUDA)

FIND_PACKAGE(CUDA)

ADD_EXECUTABLE(hello_cublas simpleCUBLAS/simpleCUBLAS.cpp)
TARGET_INCLUDE_DIRECTORIES(hello_cublas PRIVATE ${CUDA_INCLUDE_DIRS})
TARGET_LINK_LIBRARIES(hello_cublas PRIVATE ${CUDA_LIBRARIES})
TARGET_LINK_LIBRARIES(hello_cublas PRIVATE ${CUDA_CUBLAS_LIBRARIES})
