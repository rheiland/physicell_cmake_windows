add_library(CustomModulesFunctions custom.cpp)
  
target_link_libraries(CustomModulesFunctions PUBLIC proj::VectorFunctions)
