add_library(VectorFunctions BioFVM_vector.cpp)

add_library(proj::VectorFunctions ALIAS VectorFunctions)

target_include_directories(
  VectorFunctions PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>")