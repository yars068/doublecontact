# CMake buildlist for contconv
project(contconv)
cmake_minimum_required(VERSION "2.8.9")

set(CMAKE_BUILD_TYPE "Debug" CACHE STRING "" FORCE)

cmake_host_system_information(RESULT PLATFORM QUERY OS_NAME)
message(STATUS "Build host is: ${PLATFORM}")

if (${PLATFORM} MATCHES "Linux")
  if(NOT_DEFINED $ENV{CMAKE_INSTALL_PREFIX})
    set($ENV{CMAKE_INSTALL_PREFIX} "/usr/local")
  endif(NOT_DEFINED $ENV{CMAKE_INSTALL_PREFIX})
  message(STATUS "Installation prefix is ${CMAKE_INSTALL_PREFIX}")
endif(${PLATFORM} MATCHES "Linux")

#find_package(zlib)
#message(STATUS)

add_executable(
  ${PROJECT_NAME}
  main.cpp
  consoleasyncui.cpp
  consoleasyncui.h
  convertor.cpp
  convertor.h
)

install(
  TARGETS ${PROJECT_NAME}
  RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
)
