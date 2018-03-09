cmake_minimum_required(VERSION 2.6.0)

# here we specify that the project is C language only, so the default
# C compiler on the system will be used
project(gameoflife C)
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Wall" )
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Wextra" )
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Wshadow" )
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -std=c99" )

include(FindPkgConfig)

PKG_SEARCH_MODULE(SDL REQUIRED sdl)
PKG_SEARCH_MODULE(SDL_IMAGE REQUIRED SDL_image>=1.0.0)
add_executable(gameoflife gameoflife.c)

include_directories(${SDL_INCLUDE_DIRS} ${SDLIMAGE_INCLUDE_DIRS})
target_link_libraries(gameoflife ${SDL_LIBRARIES} ${SDLIMAGE_LIBRARIES} m)

INSTALL(TARGETS gameoflife DESTINATION bin)
