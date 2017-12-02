##PROJECT 
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
link_directories(${LIBRARY_OUTPUT_PATH})

#include PROJECT's include directory
include_directories(${PROJECT_SOURCE_DIR}/include)
#include MODULES's include directory
include_directories(${PROJECT_SOURCE_DIR}/modules/internal-include)


###CUR MODULE
get_filename_component(tmp_CURRENT_SOURCE_DIR_SHORT_NAME "${CMAKE_CURRENT_SOURCE_DIR}" NAME)
set(the_MODULE_NAME ${tmp_CURRENT_SOURCE_DIR_SHORT_NAME})



#build the module executable
set(${the_MODULE_NAME}_BUILD_executable  ON)
if(${the_MODULE_NAME}_BUILD_executable)
    add_executable(${the_MODULE_NAME}  ${the_MODULE_NAME}.cpp)
else()
    add_library(${the_MODULE_NAME}  ${the_MODULE_NAME}.cpp)
endif()




#if(${PROJECT_NAME}_TEST)
#    if(NOT GTEST_FOUND)
#        add_subdirectory(${PROJECT_SOURCE_DIR}/dependents/googletest LIBRARY_OUTPUT_PATH)
#        include_directories(${gtest_SOURCE_DIR}/include)
#    endif()
#endif()

#link libarary
#target_link_libraries(${the_MODULE_NAME} ${PRJECT_ROO})



