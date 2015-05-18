cmake_minimum_required(VERSION 2.8.0)
project(Lua)

mark_as_advanced(CMAKE_BACKWARDS_COMPATIBILITY)

if (POLICY CMP0011)
   cmake_policy(SET CMP0011 OLD) # or even better, NEW
endif (POLICY CMP0011)

if (NOT LUA_ROOT_DIR)
    set(LUA_ROOT_DIR ${PROJECT_SOURCE_DIR})
endif ()

# LUA_USE_APICHECK  in full debug modes

file(GLOB LUA_SOURCE ${LUA_ROOT_DIR}/src/*.c)
file(GLOB LUA_HEADER ${LUA_ROOT_DIR}/src/*.h)

if (WIN32)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

add_library(Lua STATIC ${LUA_SOURCE})

set (LUA_INCLUDE_DIR "${LUA_ROOT_DIR}/src")
include_directories("${LUA_INCLUDE_DIR}")