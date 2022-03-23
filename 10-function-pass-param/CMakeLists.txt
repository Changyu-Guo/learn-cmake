CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(function-pass-param)

FUNCTION(FUN list_in)
  MESSAGE(STATUS "in function: list_in = ${list_in}")
ENDFUNCTION()

SET(mylist "")
LIST(APPEND mylist a)
LIST(APPEND mylist b)
LIST(APPEND mylist c)

FUN(mylist)
FUN(${mylist})

FUNCTION(MY_FUN list_in)
  MESSAGE(STATUS "in my function : ARGC = ${ARGC}")
  MESSAGE(STATUS "in my function : ARGV = ${ARGV}")
ENDFUNCTION()

MY_FUN(${mylist})

