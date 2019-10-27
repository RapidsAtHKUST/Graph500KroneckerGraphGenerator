cmake_minimum_required(VERSION 3.6)
project(generator C)

set(CMAKE_C_STANDARD 11)
add_compile_options(-std=c99 -Wall -Drestrict=__restrict__ -O3 -DNDEBUG -ffast-math) # -g -pg)
include_directories(.)
link_libraries(m)

find_package(OpenMP)
set(GENERATOR_SOURCES graph_generator.c make_graph.c splittable_mrg.c utils.c)

if (OPENMP_FOUND)
    set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
    add_compile_definitions(GRAPH_GENERATOR_OMP=1)
    add_executable(generator_omp generator_omp.c ${GENERATOR_SOURCES})
else ()
    add_compile_definitions(DGRAPH_GENERATOR_SEQ=1)
    add_executable(generator_seq generator_seq.c ${GENERATOR_SOURCES})
endif ()

