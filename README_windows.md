# README_windows - edits needed to get PhysiCell to compile via CMake using native Windows Visual C++ compiler

* remove from cmake:  PhysiCell_digital_cell_line
* attempted /vector_ops to solve overloaded "<<"
* edit all overloaded "<<" (for vectors) with explicit indices (e.g., position[0], [1], [2])
* replace "unsigned int" for loop indices to be just "int" for OpenMP-related for loops
* edit main.cpp

```
M1P~/git/physicell_cmake/Windows_version/physicell_cmake$ diff main.cpp ../../main.cpp 
86,90d85
< extern std::unordered_map<std::string,int> cell_definition_indices_by_name; 
< extern std::vector<double> (*cell_division_orientation)(void) ; // = UniformOnUnitSphere; // LegacyRandomOnUnitSphere; 
```

* in modules/PhysiCell_settings.cpp, comment out (~line 222)
```
		// look for legacy_random_points_on_sphere_in_divide 
		settings = 
			xml_get_bool_value( node_options, "legacy_random_points_on_sphere_in_divide" ); 
		if( settings )
		{
			std::cout << "setting legacy unif" << std::endl; 
			// extern std::vector<double> (*cell_division_orientation)(void); 
			// cell_division_orientation = LegacyRandomOnUnitSphere; 
		}
```


```
PS C:\Users\heiland\physicell_cmake> rm -rf build
PS C:\Users\heiland\physicell_cmake> mkdir build
PS C:\Users\heiland\physicell_cmake> cd build
PS C:\Users\heiland\physicell_cmake\build> cmake ..
PS C:\Users\heiland\physicell_cmake\build> cmake --build . --config Release
Microsoft (R) Build Engine version 16.11.1+3e40a09f8 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

  Checking Build System
  Building Custom Rule C:/Users/heiland/dev/physicell_cmake/vector_ops/CMakeLists.txt
  BioFVM_vector.cpp
  VectorFunctions.vcxproj -> C:\Users\heiland\dev\physicell_cmake\build\vector_ops\Release\VectorFunctions.lib
  Building Custom Rule C:/Users/heiland/dev/physicell_cmake/BioFVM/CMakeLists.txt
  BioFVM_MultiCellDS.cpp
  BioFVM_microenvironment.cpp
```