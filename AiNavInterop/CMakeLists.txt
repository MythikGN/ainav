file(GLOB DETOUR Detour/Source/*.cpp)
file(GLOB DETOURTILE DetourTileCache/Source/*.cpp)
file(GLOB DETOURCROWD DetourCrowd/Source/*.cpp)
file(GLOB RECAST Recast/Source/*.cpp)


cmake_minimum_required(VERSION 3.20)
project(AiNav)
add_definitions(-DAINAV_EXPORTS)
add_definitions(-DLINUXBUILD)

set(CMAKE_CXX_STANDARD 14)
include_directories(DetourCrowd/Include)
include_directories(Detour/Include)
include_directories(DetourTileCache/Include)
include_directories(Recast/Include)
add_library(AiNav SHARED AiNav.cpp AiCrowd.hpp AiNav.h AiQuery.hpp Navigation.hpp NavigationBuilder.hpp NavigationMesh.hpp

        AiCrowd.cpp AiQuery.cpp NavigationBuilder.cpp NavigationMesh.cpp ${DETOUR} ${DETOURTILE} ${DETOURCROWD} ${RECAST})
