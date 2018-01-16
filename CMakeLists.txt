cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(KCF LANGUAGES CXX)

## build settings:

set(CMAKE_CXX_STANDARD 11)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release CACHE STRING "Choose the build type" FORCE)
endif()

set(CMAKE_CXX_FLAGS_RELEASE -O3)

## 3rd-party dependencies:

find_package(OpenCV REQUIRED)

## executable:

set(sources
  src/fhog.cpp
  src/kcftracker.cpp
  src/runtracker.cpp)

set(headers
  src/ffttools.hpp
  src/fhog.hpp
  src/kcftracker.hpp
  src/labdata.hpp
  src/recttools.hpp
  src/tracker.h)

add_executable(${PROJECT_NAME} ${sources} ${headers})
target_include_directories(${PROJECT_NAME} PUBLIC src)
target_link_libraries(${PROJECT_NAME} PUBLIC ${OpenCV_LIBS})
