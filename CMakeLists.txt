cmake_minimum_required(VERSION 3.5)
project(PropertyEditor)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS on)
find_package(Qt5 COMPONENTS Widgets REQUIRED)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

#添加所有的源文件

file(GLOB SOURCE_FILES ./src/*.cpp)
file(GLOB HEADER_FILES ./include/PropertyEditor/*.h)
add_library(PropertyEditor
    ${SOURCE_FILES}    
    ${HEADER_FILES} 
)
target_include_directories(PropertyEditor PUBLIC
    $<BUILD_INTERFACE:
        ${CMAKE_CURRENT_LIST_DIR}/include
        ${CMAKE_CURRENT_BINARY_DIR}/
        >
    $<INSTALL_INTERFACE:include>
)
target_link_libraries(PropertyEditor PUBLIC 
    Qt5::Widgets
)

add_subdirectory(test)
