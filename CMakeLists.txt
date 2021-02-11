
cmake_minimum_required(VERSION 2.8.12)

project(PassManager)

set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(Qt5Gui REQUIRED)
find_package(Qt5Widgets REQUIRED)
find_package(Qt5Network REQUIRED)

file(GLOB SOURCES *.cpp)
file(GLOB HEADERS *.h)

qt5_wrap_ui(UI_HEADERS mainwindow.ui)

if (WIN32)
  set(TARGET_TYPE "WIN32")
endif()

add_executable(${CMAKE_PROJECT_NAME} ${TARGET_TYPE} ${SOURCES} ${HEADERS} ${UI_HEADERS})

target_link_libraries(${CMAKE_PROJECT_NAME} Qt5::Widgets Qt5::Network)
if (UNIX)
  target_link_libraries(${CMAKE_PROJECT_NAME} -lpthread)
endif()
