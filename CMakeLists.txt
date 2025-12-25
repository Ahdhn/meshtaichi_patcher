cmake_minimum_required(VERSION 3.4...3.18)
project(meshtaichi_patcher_core LANGUAGES CXX C)

find_package(pybind11 REQUIRED)

#add_subdirectory(pybind11)
#pybind11_add_module(meshtaichi_patcher_core src/main.cpp src/api.cpp src/mesh.cpp src/patcher_old.cpp src/csr.cpp src/cluster.cpp src/patcher.cpp)

add_library(meshtaichi_patcher_core MODULE src/main.cpp src/api.cpp src/mesh.cpp src/patcher_old.cpp src/csr.cpp src/cluster.cpp src/patcher.cpp)

target_link_libraries(meshtaichi_patcher_core PRIVATE pybind11::module)

# EXAMPLE_VERSION_INFO is defined by setup.py and passed into the C++ code as a
# define (VERSION_INFO) here.
target_compile_definitions(meshtaichi_patcher_core
                           PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})
						   
set_target_properties(meshtaichi_patcher_core PROPERTIES SUFFIX ".pyd")