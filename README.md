# Shooter Game

Just trying to make an FPS game with OpenGL 3.3 and some libraries.

This was created on a Windows machine. I am trying to make sure that it runs well on Linux as well. I want to also have it running on MacOS also.

### Dependencies
- OpenGL
- GLFW
- glad
- stb_image.h
- miniaudio

### To build:
Tested on Windows 11 and Linux (WSL).

Requirements:
- CMake 
- Git
- A C++ compiler that has C++23 support

Run:
`git clone --recurse-submodules https://github.com/angeloaf20/ShooterGame.git`

`cmake -S . -B build`

`cmake --build build`