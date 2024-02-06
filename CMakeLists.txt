cmake_minimum_required(VERSION 3.13 FATAL_ERROR)

find_package(CUDAToolkit 11 REQUIRED)

project(lbvh LANGUAGES CXX CUDA)

## Use C++11
set (CMAKE_CXX_STANDARD 11)
set (CMAKE_CUDA_STANDARD 11)   


file(GLOB SRC
    "lbvh/*.h"
    "lbvh/*.cpp"
	"lbvh/*.c"
	"lbvh/*.cu"
	"lbvh/*.cuh"
	"*.h"
    "*.cpp"
	"*.c"
	"*.cu"
	)

add_executable(lbvh 
	${SRC}
)


target_compile_options(lbvh PUBLIC $<$<COMPILE_LANGUAGE:CUDA>:
                       --extended-lambda
					   --default-stream per-thread
                       >)

