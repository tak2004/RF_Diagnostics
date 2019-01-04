# Define a project if this file wasn't included.
if(NOT CMAKE_PROJECT_NAME OR "${CMAKE_PROJECT_NAME}" MATCHES "^RF_Diagnostics$")
    cmake_minimum_required(VERSION 2.8.11)
    project(RF_Diagnostics)
    # put the libraries to the dist directory
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/dist)
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/dist)
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/dist)    
endif()

include("Integrate.cmake")
rcf_addpackage(radonframework "dev")

rcf_generate(module RF_DIAGNOSTICS RadonFrameworkDiagnostics "Framework")
    rcf_add_recursive("src/" "Source")
    rcf_add_recursive("include/RadonFramework/" "Includes")
    rcf_add_public_include("${CMAKE_CURRENT_SOURCE_DIR}/include/")
    rcf_dependencies(RadonFramework)
rcf_endgenerate()