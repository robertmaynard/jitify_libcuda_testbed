

cmake_minimum_required(VERSION 3.20.0 FATAL_ERROR)

include(fetch_rapids.cmake)
include(rapids-cmake)
include(rapids-cpm)
include(rapids-cuda)
include(rapids-export)
include(rapids-find)

project(verify_libcudacxx VERSION 0.1.0 LANGUAGES CXX C CUDA)

find_package(CUDAToolkit REQUIRED)

rapids_cpm_init()
include(get_jitify.cmake)
include(make_jit_kernels.cmake)


add_executable(use_nvcc_to_verify
  use_cuda_std.cu
  use_cuda_std_and_std.cu
  use_global.cu
  use_std.cu
  main.cu)
