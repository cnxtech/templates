cmake_minimum_required(VERSION 2.8)
project(@ProjectName@)
find_package(qibuild)
qi_sanitize_compile_flags(HIDDEN_SYMBOLS)

include_directories(".")

set(@PROJECT_NAME@_PUBLIC_HEADERS
  @projectname@/@projectname@.hpp
)

set(@PROJECT_NAME@_SOURCES
  src/@projectname@.cpp
)

qi_create_lib(@projectname@ SHARED
  ${@PROJECT_NAME@_SOURCES}
)

qi_use_lib(@projectname@ QI)
qi_stage_lib(@projectname@)

qi_install_header(${@PROJECT_NAME@_PUBLIC_HEADERS} KEEP_RELATIVE_PATHS)

add_subdirectory(test)
