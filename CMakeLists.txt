cmake_minimum_required(VERSION 3.1)
project(crt C)
add_subdirectory(libc)
if(WIN32)
	add_subdirectory(win32)
endif()
set(SRCS $<TARGET_OBJECTS:ctype>)
set(SRCS ${SRCS} $<TARGET_OBJECTS:errno>)
set(SRCS ${SRCS} $<TARGET_OBJECTS:internal>)
set(SRCS ${SRCS} $<TARGET_OBJECTS:stdio>)
set(SRCS ${SRCS} $<TARGET_OBJECTS:stdlib>)
set(SRCS ${SRCS} $<TARGET_OBJECTS:string>)
if(WIN32)
	set(SRCS ${SRCS} $<TARGET_OBJECTS:win32>)
endif()
add_library(c STATIC ${SRCS})
