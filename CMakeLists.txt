﻿# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.8)

project(RawGameProgramming VERSION 0.1.0)

# Library inclusion

if (WIN32)
	set(SDL2_DIR ${CMAKE_SOURCE_DIR}/lib/cmake/SDL2-2.28.5/cmake)
endif (WIN32)

find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})


# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("RawGameProgramming")

# Add source to this project's executable.
add_executable (RawGameProgramming "src/Game.cpp" "src/Game.h" "src/Main.cpp")

target_link_libraries(RawGameProgramming ${SDL2_LIBRARIES})

