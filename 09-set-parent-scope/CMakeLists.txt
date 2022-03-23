CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(set-parent-scope)

FUNCTION(FUN xxx)
  SET(${xxx} parent_value PARENT_SCOPE)
  MESSAGE(STATUS "in function : xxx = ${xxx}")
ENDFUNCTION()

MESSAGE(STATUS "in parent xxx 1 = ${xxx}")
FUN(xxx)
MESSAGE(STATUS "in parent xxx 2 = ${xxx}")

MESSAGE(STATUS "in parent yyy 1 = ${yyy}")
FUN(yyy)
MESSAGE(STATUS "in parent yyy 2 = ${yyy}")

