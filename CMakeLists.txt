cmake_minimum_required(VERSION 3.19)

project(voro++ C CXX)

option(BUILD_VORO_EXECUTABLE "build voro executable" ON)

SET(
    LIB_VORO_SRC
    ${CMAKE_CURRENT_SOURCE_DIR}/src/c_loops.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cell.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/common.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/container_prd.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/container.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/pre_container.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/unitcell.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/v_base_wl.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/v_base.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/v_compute.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/voro++.cc
    ${CMAKE_CURRENT_SOURCE_DIR}/src/wall.cc
)

SET(
    EXEC_SRC
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cmd_line.cc
)

add_library(voro_lib STATIC ${LIB_VORO_SRC})
target_include_directories(voro_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)

IF(BUILD_VORO_EXECUTABLE)
    add_executable(voro++ ${EXEC_SRC})
    target_link_libraries(voro++ PUBLIC voro_lib)
endif(BUILD_VORO_EXECUTABLE)