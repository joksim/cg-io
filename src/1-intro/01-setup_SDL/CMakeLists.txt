
add_executable(01-setup_SDL setup_SDL.cpp)
target_link_libraries(01-setup_SDL SDL2::SDL2 SDL2::SDL2main glad)


add_executable(sdl2-image-test sdl2-image-test.cpp)
target_link_libraries(sdl2-image-test SDL2::SDL2 SDL2::SDL2main SDL2_image::SDL2_image glad)

# Copy resources to the ouptut dir
configure_file(lettuce.png lettuce.png COPYONLY)
