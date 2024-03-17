project(openecu)

set(CMAKE_C_COMPILER /tricore-gcc/bin/tricore-elf-gcc)
set(CMAKE_C_COMPILER_WORKS 1)
set(CMAKE_SHARED_LIBRARY_LINK_C_FLAGS "")
set(CMAKE_SHARED_LIBRARY_LINK_CXX_FLAGS "")
set(CMAKE_EXE_COMPILER_FLAGS "") 

add_executable(openecu 
    main.c
)