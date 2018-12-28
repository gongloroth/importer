cmake_minimum_required(VERSION 3.1.0)

project(importer)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# include_directories(./blabla)

find_package(Qt5Widgets REQUIRED)

file(GLOB_RECURSE src ./src/*.h ./src/*.cpp)
file(GLOB_RECURSE guisrc ./src/*.ui)

qt5_wrap_ui(cppguisrc $(guisrc))

set(libs pthread Qt5::Widgets Qt5::Core Qt5::Gui)

#add_library(first_qt_lib ${libsrc})

add_executable(importer ${src} ${cppguisrc})
target_link_libraries(importer ${libs})

install(TARGETS importer DESTINATION ${PROJECT_BINARY_DIR}/../Bin)
