cmake_minimum_required(VERSION 3.18.1)

project("jailbreak_root_detection")

set(can_use_assembler TRUE)

enable_language(ASM)

add_library(antifrida SHARED syscall.S antifrida.cpp)

find_library(log-lib log)

target_link_libraries(antifrida ${log-lib})

# Support for 16 KB page sizes (required for Google Play Store)
# This ensures the library is aligned for 16KB page sizes (also compatible with 4KB)
set(CMAKE_ANDROID_PAGE_SIZE 16384)
