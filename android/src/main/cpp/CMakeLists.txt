cmake_minimum_required(VERSION 3.22.1)

project("toolChecker" C CXX ASM)

# Use clang toolchain only, avoid deprecated flags
set(CMAKE_C_COMPILER_LAUNCHER "")
set(CMAKE_CXX_COMPILER_LAUNCHER "")

# Enable ASM language support
enable_language(ASM)

# Build shared library named toolChecker
add_library(toolChecker SHARED
    syscall.S
    antifrida.cpp
)

# Find and link log library
find_library(log-lib log)

target_link_libraries(toolChecker ${log-lib})

# Set C++ standard
set_property(TARGET toolChecker PROPERTY CXX_STANDARD 11)
set_property(TARGET toolChecker PROPERTY CXX_STANDARD_REQUIRED ON)
