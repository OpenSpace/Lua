cmake_minimum_required(VERSION 2.8.0)
project(Lua)

mark_as_advanced(CMAKE_BACKWARDS_COMPATIBILITY)

if (POLICY CMP0011)
   cmake_policy(SET CMP0011 OLD) # or even better, NEW
endif (POLICY CMP0011)

if (NOT LUA_ROOT_DIR)
    set(LUA_ROOT_DIR ${PROJECT_SOURCE_DIR})
endif ()

# LUA_USE_APICHECK  in full debug modess

set (LUA_SOURCE
    ${LUA_ROOT_DIR}/src/lapi.c
    ${LUA_ROOT_DIR}/src/lauxlib.c
    ${LUA_ROOT_DIR}/src/lbaselib.c
    ${LUA_ROOT_DIR}/src/lbitlib.c
    ${LUA_ROOT_DIR}/src/lcode.c
    ${LUA_ROOT_DIR}/src/lcorolib.c
    ${LUA_ROOT_DIR}/src/lctype.c
    ${LUA_ROOT_DIR}/src/ldblib.c
    ${LUA_ROOT_DIR}/src/ldebug.c
    ${LUA_ROOT_DIR}/src/ldo.c
    ${LUA_ROOT_DIR}/src/ldump.c
    ${LUA_ROOT_DIR}/src/lfunc.c
    ${LUA_ROOT_DIR}/src/lgc.c
    ${LUA_ROOT_DIR}/src/linit.c
    ${LUA_ROOT_DIR}/src/liolib.c
    ${LUA_ROOT_DIR}/src/llex.c
    ${LUA_ROOT_DIR}/src/lmathlib.c
    ${LUA_ROOT_DIR}/src/lmem.c
    ${LUA_ROOT_DIR}/src/loadlib.c
    ${LUA_ROOT_DIR}/src/lobject.c
    ${LUA_ROOT_DIR}/src/lopcodes.c
    ${LUA_ROOT_DIR}/src/loslib.c
    ${LUA_ROOT_DIR}/src/lparser.c
    ${LUA_ROOT_DIR}/src/lstate.c
    ${LUA_ROOT_DIR}/src/lstring.c
    ${LUA_ROOT_DIR}/src/lstrlib.c
    ${LUA_ROOT_DIR}/src/ltable.c
    ${LUA_ROOT_DIR}/src/ltablib.c
    ${LUA_ROOT_DIR}/src/ltm.c
    ${LUA_ROOT_DIR}/src/lundump.c
    ${LUA_ROOT_DIR}/src/lvm.c
    ${LUA_ROOT_DIR}/src/lzio.c
    )

set (LUA_HEADER
    ${LUA_ROOT_DIR}/include/lapi.h
    ${LUA_ROOT_DIR}/include/lauxlib.h
    ${LUA_ROOT_DIR}/include/lcode.h
    ${LUA_ROOT_DIR}/include/lctype.h
    ${LUA_ROOT_DIR}/include/ldebug.h
    ${LUA_ROOT_DIR}/include/ldo.h
    ${LUA_ROOT_DIR}/include/lfunc.h
    ${LUA_ROOT_DIR}/include/lgc.h
    ${LUA_ROOT_DIR}/include/llex.h
    ${LUA_ROOT_DIR}/include/llimits.h
    ${LUA_ROOT_DIR}/include/lmem.h
    ${LUA_ROOT_DIR}/include/lobject.h
    ${LUA_ROOT_DIR}/include/lopcodes.h
    ${LUA_ROOT_DIR}/include/lparser.h
    ${LUA_ROOT_DIR}/include/lstate.h
    ${LUA_ROOT_DIR}/include/lstring.h
    ${LUA_ROOT_DIR}/include/ltable.h
    ${LUA_ROOT_DIR}/include/ltm.h
    ${LUA_ROOT_DIR}/include/lua.h
    ${LUA_ROOT_DIR}/include/lua.hpp.h
    ${LUA_ROOT_DIR}/include/luaconf.h
    ${LUA_ROOT_DIR}/include/lualib.h
    ${LUA_ROOT_DIR}/include/lundump.h
    ${LUA_ROOT_DIR}/include/lvm.h
    ${LUA_ROOT_DIR}/include/lzio.h
    )

if (WIN32)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

add_library(Lua STATIC ${LUA_SOURCE})

set (LUA_INCLUDE_DIR "${LUA_ROOT_DIR}/include")
include_directories("${LUA_INCLUDE_DIR}")