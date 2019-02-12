cmake_minimum_required(VERSION 2.8.3)

project(kdl_parser)
include_directories(include)
add_compile_options(-std=c++11)

add_library(${PROJECT_NAME} SHARED
    src/kdl_parser.cpp
)

target_link_libraries(${PROJECT_NAME}
  tinyxml2 orocos-kdl
)

add_executable(check_kdl_parser src/check_kdl_parser.cpp )
target_link_libraries(check_kdl_parser ${PROJECT_NAME} tinyxml2 urdfdom_model)


#install(TARGETS ${PROJECT_NAME}
#  DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION})

#install(DIRECTORY include/${PROJECT_NAME}/
#  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

install(DIRECTORY include/
        DESTINATION /usr/local/include
        FILES_MATCHING PATTERN "*.hpp")

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION /usr/local/lib)
