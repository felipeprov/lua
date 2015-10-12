
option(GEN_COMPILER "Lua Compiler" ON)
option(GEN_INTERPRETER "Lua Interpreter" ON)

add_library(lual lapi.c lauxlib.c lbaselib.c lbitlib.c lcode.c lcorolib.c lctype.c ldblib.c ldebug.c ldo.c ldump.c lfunc.c lgc.c linit.c liolib.c llex.c lmathlib.c lmem.c loadlib.c lobject.c lopcodes.c loslib.c lparser.c lprefix.h lstate.c lstring.c lstrlib.c ltable.c ltablib.c ltm.c lundump.c lutf8lib.c lvm.c lzio.c)

target_include_directories (lua_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if (${GEN_COMPILER}) 
	add_executable(luac luac.c)
	target_link_libraries(luac lual)
	
endif()


if ( ${GEN_INTERPRETER} )
	add_executable(lua lua.c)
	target_link_libraries(lua lual)
endif()
