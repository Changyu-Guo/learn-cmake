CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(02_hello_world_static_library)

SET(STATIC_LIB_SOURCES src/Hello.cpp)
SET(EXE_SOURCES src/main.cpp)

ADD_LIBRARY(hello_world_static_library STATIC ${STATIC_LIB_SOURCES})
TARGET_INCLUDE_DIRECTORIES(hello_world_static_library PUBLIC ${PROJECT_SOURCE_DIR}/include)

ADD_EXECUTABLE(hello_world ${EXE_SOURCES})
TARGET_INCLUDE_DIRECTORIES(hello_world PRIVATE ${PROJECT_SOURCE_DIR}/include)
TARGET_LINK_LIBRARIES(hello_world PRIVATE hello_world_static_library)

