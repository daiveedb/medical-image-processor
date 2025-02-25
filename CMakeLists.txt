cmake_minimum_required(VERSION 3.10)
project(MedicalImageProcessor)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find required packages
find_package(CURL REQUIRED)

# Find nlohmann_json
find_path(JSON_INCLUDE_DIR nlohmann/json.hpp
    PATHS
    /usr/local/include
    /opt/homebrew/include
)
include_directories(${JSON_INCLUDE_DIR})

# Add executable
add_executable(MedicalImageProcessor main.cpp)

# Link libraries
target_link_libraries(MedicalImageProcessor PRIVATE 
    ${CURL_LIBRARIES}
)