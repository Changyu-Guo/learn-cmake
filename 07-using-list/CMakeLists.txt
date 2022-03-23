CMAKE_MINIMUM_REQUIRED(VERSION 3.10)

PROJECT(using-list)

SET(mylist)

LIST(APPEND mylist a)
LIST(APPEND mylist b)
LIST(APPEND mylist c)

LIST(LENGTH mylist mylen)

MESSAGE(STATUS "mylist = ${mylist}")
MESSAGE(STATUS "mylist = ${mylen}")

SET(revlist ${mylist})
MESSAGE(STATUS "revlist = ${revlist}")

LIST(REVERSE revlist)
MESSAGE(STATUS "revlist = ${revlist}")

SET(t_name)
SET(t_value)

LIST(APPEND t_name xxx)
LIST(APPEND t_value 1)
LIST(APPEND t_name yyy)
LIST(APPEND t_value 2)

MESSAGE(STATUS "t_name = ${t_name}")
MESSAGE(STATUS "t_value = ${t_value}")

LIST(LENGTH t_name len)
MATH(EXPR my_len "${len} - 1")
MESSAGE(STATUS "len = ${len}")

FOREACH(val RANGE ${my_len})
  LIST(GET t_name ${val} val1)
  LIST(GET t_value ${val} val2)
  MESSAGE(STATUS "${val1} ${val2}")
ENDFOREACH()

