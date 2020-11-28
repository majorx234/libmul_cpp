cmake_minimum_required (VERSION 2.8.11)
project (libmul_cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# set header files
set(headers include/mul.h)

# set source files
set(sources src/mul.cpp)

add_library (mul_cpp SHARED
  ${sources}
  ${headers}
)

install(TARGETS mul_cpp DESTINATION lib)
install(FILES ${headers} DESTINATION include/libmul_cpp)
