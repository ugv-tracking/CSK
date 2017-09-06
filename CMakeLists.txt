cmake_minimum_required(VERSION 3.2)
if(NOT CMAKE_VERSION VERSION_LESS 3.1)
    set(CMAKE_CXX_STANDARD 11)
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# Define project name
project(CSK)

# Find OpenCV path
find_package(OpenCV REQUIRED)
message(STATUS "OpenCV library status:")
message(STATUS "    version:      ${OpenCV_VERSION}")
message(STATUS "    libraries:    ${OpenCV_LIBS}")
message(STATUS "    include_path: ${OpenCV_INCLUDE_DIRS}")

# Add OpenCV headers
include_directories(${OpenCV_INCLUDE_DIRS})

# Declare the executable target build from src
add_executable(main 
  src/main.cpp
  src/csk.cpp 
  src/csk.h 
  src/benchmark_info.cpp
  src/benchmark_info.h
  #src/run_tracker.cpp
)

# Link your application with OpenCV libraries
target_link_libraries(main ${OpenCV_LIBS})
