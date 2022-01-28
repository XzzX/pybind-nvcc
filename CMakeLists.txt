cmake_minimum_required(VERSION 3.4...3.18)
project(example LANGUAGES CXX)

find_package(Kokkos REQUIRED)

include(FetchContent)
FetchContent_Declare(
        pybind11
        GIT_REPOSITORY https://github.com/pybind/pybind11.git
        GIT_TAG v2.9.0
)
FetchContent_MakeAvailable(pybind11)

pybind11_add_module(example example.cpp)
target_link_libraries(example PRIVATE Kokkos::kokkos)
