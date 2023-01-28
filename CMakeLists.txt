cmake_minimum_required(VERSION 3.0.0)
project(app VERSION 0.1.0)

include(CTest)
enable_testing()

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /std:c++20")
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++2a -pthread -fconcepts")
endif()

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/app)
set(Boost_USE_STATIC_LIBS        ON)
set(Boost_USE_MULTITHREADED      ON)
set(Boost_USE_STATIC_RUNTIME    OFF)
find_package(Boost 1.81.0 COMPONENTS system REQUIRED)

if(Boost_FOUND)
    message("Boost found")
    message(${Boost_INCLUDE_DIRS})
    include_directories(${Boost_INCLUDE_DIRS}) 
    LINK_DIRECTORIES(${Boost_LIBRARY_DIR})
    add_executable(app main.cpp CommandLineParser.cpp CommandLineParser.h)

    target_link_libraries(app ${Boost_LIBRARIES})
else()
    message(STATUS "Boost not found !")
endif()

