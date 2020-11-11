cmake_minimum_required(VERSION 3.10)

set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -u ANativeActivity_onCreate")

set(OPTION_USE_SYSTEM_LIBPNG OFF CACHE BOOL " " FORCE)
set(OPTION_USE_SYSTEM_LIBJPEG OFF CACHE BOOL " " FORCE)
set(OPTION_USE_SYSTEM_ZLIB OFF CACHE BOOL " " FORCE)
set(OPTION_USE_GL OFF CACHE BOOL " " FORCE)
set(FLTK_BUILD_EXAMPLES OFF CACHE BOOL " " FORCE)
set(FLTK_BUILD_TEST OFF CACHE BOOL " " FORCE)
set(FLTK_BUILD_FLUID OFF CACHE BOOL " " FORCE)
set(OPTION_USE_THREADS ON CACHE BOOL " " FORCE)
set(OPTION_LARGE_FILE ON CACHE BOOL " " FORCE)
set(OPTION_BUILD_HTML_DOCUMENTATION OFF CACHE BOOL " " FORCE)
set(OPTION_BUILD_PDF_DOCUMENTATION OFF CACHE BOOL " " FORCE)

add_subdirectory(cfltk)

add_library(native-lib SHARED native-lib.c)
target_include_directories(native-lib PRIVATE cfltk/include)
target_link_libraries(native-lib PRIVATE cfltk fltk fltk_images fltk_jpeg fltk_z fltk_png)
target_link_libraries(native-lib PUBLIC log android)
