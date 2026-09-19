# CMake Project

A minimal **CMake + GLFW** starter: a C++ program that prints a message and opens a small GLFW window. GLFW is pulled in as a git submodule, and CMake fetches the submodule automatically during configuration.

## Requirements

- CMake 3.16.3 or newer
- A C++ compiler, and Ninja on Windows (the build files select the Ninja generator there)
- Git
- On Linux, the development packages GLFW itself needs; see the [GLFW compile guide](https://www.glfw.org/docs/latest/compile.html)

## Build and run

### Windows

1. `choco install cmake`
2. `choco install mingw`
3. `cmake -S . -B ./build -G "Ninja"`
4. `cmake --build build`
5. `./build/bin/cmake_project.exe`

### Linux (Ubuntu)

1. `sudo apt-get install build-essential gdb`
2. `cmake -S . -B ./build`
3. `cmake --build build`
4. `./build/bin/cmake_project`

## Submodule

GLFW lives in `external/glfw`. The submodule was added with:

```bash
git submodule add git@github.com:glfw/glfw.git external/glfw
```

`CMakeLists.txt` runs `git submodule update --init --recursive` on configure and stops with an error if the GLFW sources are missing.

## CMake notes

- `add_subdirectory()`: build a dependency as part of this project.
- `target_include_directories()`: add include paths so headers can be found with short paths.
- `target_link_directories()`: add library search directories.

## Useful

- `cmake --help` lists the available generators.
- [Configure VS Code for MinGW](https://code.visualstudio.com/docs/cpp/config-mingw)
- In VS Code, run *C/C++: Edit Configurations* to add a custom include path.
- Debug configurations for Windows and Linux are in `.vscode/`.
