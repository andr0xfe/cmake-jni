cmake_minimum_required(VERSION 3.0.0)

get_filename_component(tmp_CURRENT_SOURCE_DIR_SHORT_NAME "${CMAKE_CURRENT_SOURCE_DIR}" NAME)
project(${tmp_CURRENT_SOURCE_DIR_SHORT_NAME} VERSION 0.0.0)



option(${PROJECT_NAME}_GTEST "googletest support." OFF)


add_subdirectory(modules)



if(${PROJECT_NAME}_GTEST)
    add_subdirectory(test)
endif(${PROJECT_NAME}_GTEST)




