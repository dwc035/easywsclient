
set (TARGET_NAME easywsclient)

cmake_minimum_required (VERSION 3.8)
set (CMAKE_CXX_STANDARD 17)

# include(GNUInstallDirs)

############ Paths
set (EASYWSCLIENT_ROOT ${CMAKE_CURRENT_SOURCE_DIR})
set (EASYWSCLIENT_INCLUDE ${EASYWSCLIENT_ROOT})
set (EASYWSCLIENT_BUILD_ROOT ${CMAKE_CURRENT_BINARY_DIR})
set (EASYWSCLIENT_BIN ${EASYWSCLIENT_BUILD_ROOT}/bin)
set (EASYWSCLIENT_LIB ${EASYWSCLIENT_BUILD_ROOT}/lib)

# CMake install step prefix. I assume linux users want the prefix to
# be the default /usr or /usr/local so this is only adjusted on Windows.
# This must be set prior to any call to project or it will not be read correctly.
# - Windows: Build the INSTALL project in your solution file.
# - Linux/OSX: make install.
#if (WIN32)
#    set (CMAKE_INSTALL_PREFIX "${EASYWSCLIENT_ROOT}/install" CACHE PATH "")
#endif ()


project(${TARGET_NAME})
message(STATUS "\nGenerating make files for ${TARGET_NAME}\n")


file (GLOB EASYWSCLIENT_SOURCE ${EASYWSCLIENT_INCLUDE}/easywsclient.cpp)
file (GLOB EASYWSCLIENT_H ${EASYWSCLIENT_INCLUDE}/easywsclient.h)

add_library(${TARGET_NAME} STATIC ${EASYWSCLIENT_SOURCE})

target_include_directories(${TARGET_NAME} PUBLIC ${EASYWSCLIENT_INCLUDE} )

