
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

add_executable(test_prop
    ./main.cpp
    ./testwidget.h
    ./testwidget.cpp
    ./testwidget.ui
    ./testwidget.qrc
    )
include_directories(${CMAKE_CURRENT_BINARY_DIR})
target_include_directories(test_prop 
    PUBLIC ${CMAKE_CURRENT_BINARY_DIR})
target_link_libraries(test_prop PRIVATE PropertyEditor)
