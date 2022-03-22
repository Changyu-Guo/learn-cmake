CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(04-static-shared-library)

SET(STATIC_LIB_SOURCES src/Hello_Static.cpp)
SET(SHARED_LIB_SOURCES src/Hello_Shared.cpp)
SET(EXE_SOURCES src/main.cpp)

ADD_LIBRARY(hello_world_static_library STATIC ${STATIC_LIB_SOURCES})
ADD_LIBRARY(hello_world_shared_library SHARED ${SHARED_LIB_SOURCES})

TARGET_INCLUDE_DIRECTORIES(hello_world_static_library PUBLIC ${PROJECT_SOURCE_DIR}/include)
TARGET_INCLUDE_DIRECTORIES(hello_world_shared_library PUBLIC ${PROJECT_SOURCE_DIR}/include)

ADD_EXECUTABLE(hello_world_static ${EXE_SOURCES})

# TARGET_INCLUDE_DIRECTORIES(hello_world_static PRIVATE ${PROJECT_SOURCE_DIR}/include)
TARGET_LINK_LIBRARIES(hello_world_static PRIVATE hello_world_static_library)

ADD_EXECUTABLE(hello_world_shared ${EXE_SOURCES})

# TARGET_INCLUDE_DIRECTORIES(hello_world_shared PRIVATE ${PROJECT_SOURCE_DIR}/include)
TARGET_LINK_LIBRARIES(hello_world_shared PRIVATE hello_world_shared_library)

