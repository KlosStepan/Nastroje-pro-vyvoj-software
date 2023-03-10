cmake_minimum_required(VERSION 3.5)

project(mydb)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)

# Add sources
set(SOURCES
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

# Add headers
set(HEADERS
    data.h
    linklist.h
    textfileio.h
)

# Add executables
add_executable(testclient testclient.c)
add_executable(testserver testserver.c)
add_executable(testadmin testadmin.c)

# Add libraries
add_library(mydb STATIC ${SOURCES} ${HEADERS})

# Link readline and history libraries
find_library(READLINE_LIBRARY readline)
find_library(HISTORY_LIBRARY history)
target_link_libraries(testclient mydb ${READLINE_LIBRARY} ${HISTORY_LIBRARY})
target_link_libraries(testserver mydb ${READLINE_LIBRARY} ${HISTORY_LIBRARY})
target_link_libraries(testadmin mydb ${READLINE_LIBRARY} ${HISTORY_LIBRARY})

# Add include directories
target_include_directories(mydb PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

# Add compilation flags
target_compile_options(mydb PRIVATE ${CMAKE_C_FLAGS})
