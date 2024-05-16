cmake_minimum_required (VERSION 3.6)
project (libmul_cpp
  DESCRIPTION "a library example to learn CMake"
  VERSION 0.1.0
  LANGUAGES CXX)

include(GNUInstallDirs)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# set header files
set(LIBMUL_HEADERS include/mul.h)

# set source files
set(LIBMUL_SOURCES src/mul.cpp)

add_library (mul_cpp SHARED)
target_sources(mul_cpp
 PRIVATE
  ${LIBMUL_SOURCES}
  ${LIBMUL_HEADERS}
)

# install section (optional)
install(FILES ${LIBMUL_HEADERS} DESTINATION include/libmul_cpp)

install(TARGETS
        mul_cpp
    EXPORT mul_cppConfig
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

# create cmake script to find libmul_cpp in other projects
export(TARGETS
        mul_cpp
    NAMESPACE mul_cpp::
    FILE "${CMAKE_CURRENT_BINARY_DIR}/mul_cppConfig.cmake"
)

# install created cmake script in system's cmake folder
install(EXPORT
        mul_cppConfig
    DESTINATION "${CMAKE_INSTALL_DATADIR}/cmake/mul_cpp"
    NAMESPACE mul_cpp::
)
