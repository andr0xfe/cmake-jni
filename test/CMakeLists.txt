##PROJECT 
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
link_directories(${LIBRARY_OUTPUT_PATH})

#include PROJECT's include directory
include_directories(${PROJECT_SOURCE_DIR}/include)





# find or add googletest
if(NOT GTEST_FOUND)
    add_subdirectory(${PROJECT_SOURCE_DIR}/dependences/googletest ${PROJECT_BINARY_DIR}/dependences/googletest)
    include_directories(${gtest_SOURCE_DIR}/include)
endif()

enable_testing()

# add all runUnitTests
foreach(MODULE_NAME_TEST ${CMAKE_CURRENT_SOURCE_DIR})
    if(IS_DIRECTORY  ${MODULE_NAME_TEST})
    else()
        get_filename_component(MODULE_NAME "${MODULE_NAME_TEST}" NAME_WE)
        add_executable(${MODULE_NAME}  ${MODULE_NAME}.cpp)
        string(REPLACE "_test" "" MODULE_NAME_WE ${MODULE_NAME})
        target_link_libraries(runUnitTest_${MODULE_NAME}  gtest gtest_main  ${MODULE_NAME_WE})
    endif()
endforeach()







