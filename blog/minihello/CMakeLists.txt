cmake_minimum_required (VERSION 3.8)

set(NAME minihello)
project (${NAME})

set(CMAKE_CXX_STANDARD 17)

include_directories(
    ../../telexlib/include
    include
)

find_package (telex REQUIRED PATHS ../..)

add_executable(${PROJECT_NAME}
    src/main.cpp
    gui/${NAME}.html
    )

file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/gui/minihello.html
    DESTINATION ${CMAKE_CURRENT_BINARY_DIR}
    )

addResource(PROJECT ${PROJECT_NAME} TARGET include/${NAME}_resource.h SOURCES gui/${NAME}.html)

target_link_libraries (${PROJECT_NAME} telex)



