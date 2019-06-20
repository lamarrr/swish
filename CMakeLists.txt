cmake_minimum_required(VERSION 3.10)
project(ProjectSwish VERSION 0.1.2)

find_package(CURL REQUIRED)

if(CURL_FOUND)
message("Found CURL")
else()
message(FATAL_ERROR "Please install libcurl")
endif()

add_library(Swish INTERFACE)


target_link_libraries(Swish INTERFACE CURL)

install(DIRECTORY swish DESTINATION include)