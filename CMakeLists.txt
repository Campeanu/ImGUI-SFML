cmake_minimum_required(VERSION 3.8)

set(This ImGUI-SFAPI)

set(HEADERS
    imconfig-SFML.h
    imgui-SFML_export.h
    imgui-SFML.h
)

set(SOURCES
    imgui-SFML.cpp
)

# Linking SFML libarary.
include_directories(${SFML}/include)
link_directories(${SFML}/lib)

add_library(${This} STATIC ${SOURCES} ${HEADERS})

target_link_libraries(${This} PUBLIC
    sfml-graphics-d
    sfml-audio-d
    sfml-network-d
    sfml-window-d
    sfml-system-d
    opengl32
    ImGUI
)

target_include_directories(${This} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

set_target_properties(${This} PROPERTIES
    FOLDER Libraries
)