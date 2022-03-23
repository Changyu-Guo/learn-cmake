CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(05-static-shared-library-ext)

SET(LIB_SOURCES src/Hello.cpp)
SET(EXE_SOURCES src/main.cpp)

ADD_LIBRARY(hello_world_static_library STATIC ${LIB_SOURCES})
ADD_LIBRARY(hello_world_shared_library SHARED ${LIB_SOURCES})

TARGET_COMPILE_DEFINITIONS(hello_world_static_library PRIVATE MY_STATIC)
TARGET_INCLUDE_DIRECTORIES(hello_world_static_library PUBLIC ${PROJECT_SOURCE_DIR}/include)
TARGET_INCLUDE_DIRECTORIES(hello_world_shared_library PUBLIC ${PROJECT_SOURCE_DIR}/include)

ADD_EXECUTABLE(hello_world_link_static ${EXE_SOURCES})
# TARGET_INCLUDE_DIRECTORIES(hello_world_link_static PRIVATE ${PROJECT_SOURCE_DIR}/include)
TARGET_LINK_LIBRARIES(hello_world_link_static PRIVATE hello_world_static_library)

ADD_EXECUTABLE(hello_world_link_shared ${EXE_SOURCES})
# TARGET_INCLUDE_DIRECTORIES(hello_world_link_shared ${PROJECT_SOURCE_DIR}/include)
TARGET_LINK_LIBRARIES(hello_world_link_shared PRIVATE hello_world_shared_library)

