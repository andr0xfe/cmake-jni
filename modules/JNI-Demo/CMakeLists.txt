##PROJECT 
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)
link_directories(${LIBRARY_OUTPUT_PATH})

#include PROJECT's include directory
include_directories(${PROJECT_SOURCE_DIR}/include)
#include MODULES's include directory
include_directories(${PROJECT_SOURCE_DIR}/modules/internal-include)

# 加入REQUIRED 参数,如果找不到JNI,就报错退出
find_package(JNI REQUIRED)
# 加入jni支持
include_directories(${JAVA_INCLUDE_PATH})
include_directories(${JAVA_INCLUDE_PATH2})

###CUR MODULE
get_filename_component(tmp_CURRENT_SOURCE_DIR_SHORT_NAME "${CMAKE_CURRENT_SOURCE_DIR}" NAME)
set(the_MODULE_NAME ${tmp_CURRENT_SOURCE_DIR_SHORT_NAME})



#build the module executable
add_library(${the_MODULE_NAME} SHARED ${the_MODULE_NAME}.cpp)





#if(${PROJECT_NAME}_TEST)
#    if(NOT GTEST_FOUND)
#        add_subdirectory(${PROJECT_SOURCE_DIR}/dependents/googletest LIBRARY_OUTPUT_PATH)
#        include_directories(${gtest_SOURCE_DIR}/include)
#    endif()
#endif()

#link libarary
#target_link_libraries(${the_MODULE_NAME} ${PRJECT_ROO})



