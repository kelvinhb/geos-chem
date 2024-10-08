# KPP/fullchem/CMakeLists.txt

#----------------------------------------------------------------------------
# Add libKPPStandalone.a -- KPP standalone executable
#----------------------------------------------------------------------------
add_library(KPPStandalone
  STATIC EXCLUDE_FROM_ALL
  kpp_standalone.F90
  kpp_standalone_init.F90
)

# Dependencies
target_link_libraries(KPPStandalone
  PUBLIC
  KPP
)

# Treat REAL as if it were REAL*8
target_compile_options(KPPStandalone
  PRIVATE ""
  $<$<STREQUAL:"${CMAKE_Fortran_COMPILER_ID}","Intel">:-r8>
  $<$<STREQUAL:"${CMAKE_Fortran_COMPILER_ID}","GNU">:-fdefault-real-8 -fdefault-double-8>
)
