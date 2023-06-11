cmake_minimum_required(VERSION 3.20)

project(cg-io)

# Fetch all the libraries needed for the project
include(FetchContent)
Set(FETCHCONTENT_QUIET FALSE)

# set(BUILD_SHARED_LIBS TRUE)

FetchContent_Declare(
        SDL2
        GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
        GIT_TAG release-2.26.5
        GIT_SHALLOW TRUE
        GIT_PROGRESS TRUE
)
set(SDL2_INSTALL OFF)
FetchContent_MakeAvailable(SDL2)


# SDL2 Image
FetchContent_Declare(
        SDL2_image
        GIT_REPOSITORY https://github.com/libsdl-org/SDL_image.git
        GIT_TAG release-2.6.3
        GIT_SHALLOW TRUE
        GIT_PROGRESS TRUE
)
set(SDL2IMAGE_INSTALL OFF)

#set(BUILD_SHARED_LIBS FALSE)

FetchContent_MakeAvailable(SDL2_image)

# GLAD
FetchContent_Declare(
        glad
        GIT_REPOSITORY https://github.com/Dav1dde/glad.git
)
FetchContent_GetProperties(glad)
if(NOT glad_POPULATED)
    FetchContent_Populate(glad)
    set(GLAD_PROFILE "core" CACHE STRING "OpenGL profile")
    set(GLAD_API "gl=" CACHE STRING "API type/version pairs, like \"gl=3.2,gles=\", no version means latest")
    set(GLAD_GENERATOR "c" CACHE STRING "Language to generate the binding for")
    add_subdirectory(${glad_SOURCE_DIR} ${glad_BINARY_DIR})
endif()



add_subdirectory(src)
add_executable(sdl_test_check main.cpp)
target_link_libraries(sdl_test_check SDL2::SDL2main SDL2::SDL2 SDL2_image::SDL2_image glad)


