cmake_minimum_required(VERSION 3.10)

project(mydb)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED True)

# Compile flags
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -Wextra -pedantic")

# Source files
set(SRC
    btree_int.c
    client_comm.c
    conds.c
    config.c
    data.c
    db_engine.c
    db_main.c
    error.c
    index.c
    memory.c
    parser_commands.c
    parser_conds.c
    query.c
    result.c
    server_comm.c
    sql_parser.c
    strutil.c
    tabconf.c
    tabdef.c
    textfileio.c
)

# Library
add_library(mydb STATIC ${SRC})

# Headers
target_include_directories(mydb PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

# Test clients
add_executable(testclient testclient.c)
target_link_libraries(testclient mydb readline)

add_executable(testserver testserver.c)
target_link_libraries(testserver mydb readline)

add_executable(testadmin testadmin.c)
target_link_libraries(testadmin mydb readline)

# Clean
add_custom_target(clean-all
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_CURRENT_BINARY_DIR}/libmydb.a
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_CURRENT_BINARY_DIR}/testclient
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_CURRENT_BINARY_DIR}/testserver
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_CURRENT_BINARY_DIR}/testadmin
    COMMAND ${CMAKE_COMMAND} -E remove ${CMAKE_CURRENT_BINARY_DIR}/*.o
)
