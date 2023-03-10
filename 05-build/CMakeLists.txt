cmake_minimum_required(VERSION 3.0)
project(mydb C)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -Wall")

add_subdirectory(src)

add_custom_target(all
    COMMAND ${CMAKE_MAKE_PROGRAM} all
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src
)

add_custom_target(testclient
    COMMAND ${CMAKE_MAKE_PROGRAM} testclient
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src
)

add_custom_target(testserver
    COMMAND ${CMAKE_MAKE_PROGRAM} testserver
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src
)

add_custom_target(testadmin
    COMMAND ${CMAKE_MAKE_PROGRAM} testadmin
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src
)

add_custom_target(clean
    COMMAND ${CMAKE_MAKE_PROGRAM} clean
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src
)
