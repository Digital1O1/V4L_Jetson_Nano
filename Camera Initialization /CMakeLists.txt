cmake_minimum_required(VERSION 3.10)
project(CaptureImx219)

# Find the required packages
find_package(OpenCV REQUIRED)

# Set the source files for your project
set(SOURCES main.cpp)

# Add the executable target
add_executable(${PROJECT_NAME} ${SOURCES})

# Link against the required libraries
target_link_libraries(${PROJECT_NAME}
    PRIVATE
        # Link against the V4L2 library
        v4l2
        # Link against OpenCV
        ${OpenCV_LIBS}
)

# Set compiler flags
target_compile_options(${PROJECT_NAME}
    PRIVATE
        -Wall
        -Wextra
        # Add other compiler flags if needed
)

# Set include directories
target_include_directories(${PROJECT_NAME}
    PRIVATE
        # Add include directories if needed
)

# Set the C++ standard
set_target_properties(${PROJECT_NAME} PROPERTIES
    CXX_STANDARD 11
    CXX_STANDARD_REQUIRED YES
)

# Set output directories
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
