cmake_minimum_required(VERSION 3.26)
project(QJoysticks)

set(CMAKE_CXX_STANDARD 14)
add_compile_definitions(SDL_SUPPORTED)
set(CMAKE_AUTOMOC ON)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 COMPONENTS Quick Widgets QuickControls2 REQUIRED)

#find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Widgets)
#find_package(Qt6 REQUIRED COMPONENTS Widgets)

include_directories(lib/SDL/include)
include_directories(src)
include_directories(src/QJoysticks)

qt_add_library(QJoysticks
        src/QJoysticks/Android_Joystick.cpp
        src/QJoysticks/SDL_Joysticks.cpp
        src/QJoysticks/VirtualJoystick.cpp
        src/QJoysticks.cpp)

qt_add_executable(QJoysticks_example
        examples/JoystickList/main.cpp
        examples/JoystickList/main.qml
        examples/JoystickList/qml.qrc)

target_link_libraries(QJoysticks_example PRIVATE QJoysticks Qt6::Quick Qt6::Widgets)
target_link_libraries(QJoysticks
        PRIVATE Qt6::Quick Qt6::Widgets Qt6::QuickControls2 SDL2)