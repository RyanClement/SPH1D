cmake_minimum_required(VERSION 3.0.0)

project(SPH1D VERSION 1.0
        DESCRIPTION "Shock Tube"
        LANGUAGES CXX)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Commented out. Let user specify with flag.
# Specify the build type
#set(CMAKE_BUILD_TYPE Release)
#set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS_RELEASE})

# Future Testing Capability ...
#include(CTest)
#enable_testing()

#set(CPACK_PROJECT_NAME ${PROJECT_NAME})
#set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
#include(CPack)

include_directories(inc)
set(SOURCES
        src/artVisc.cpp
        src/conDen.cpp
        src/DataOut.cpp
        src/dtStep.cpp
        src/gasEOS.cpp
        src/init.cpp
        src/internalForces.cpp
        src/skCubSpl.cpp
        src/skGauss.cpp
        src/sph1D.cpp
        src/sumDen.cpp
        src/symFind.cpp
        src/timeIntegrator.cpp
        src/Timer.cpp
        src/waterEOS.cpp
)

# System/Compiler Independent Settings
if ("Windows" STREQUAL ${CMAKE_HOST_SYSTEM_NAME})
        message("***** OS: Windows")
        add_executable(SPH1D ${SOURCES})
elseif("Linux" STREQUAL ${CMAKE_HOST_SYSTEM_NAME})
        message("***** OS: Linux")
        add_executable(SPH1D.x ${SOURCES})
endif()

# Print some CMake Variables for the User
message("CMAKE_HOST_SYSTEM_NAME = " ${CMAKE_HOST_SYSTEM_NAME})
message("CMAKE_CXX_COMPILER_ID = " ${CMAKE_CXX_COMPILER_ID})
message("CMAKE_BUILD_TYPE = " ${CMAKE_BUILD_TYPE})
message("CMAKE_CXX_FLAGS = " ${CMAKE_CXX_FLAGS})

# Print CMake Variables
#get_cmake_property(_variableNames VARIABLES)
# list (SORT _variableNames)
# foreach (_variableName ${_variableNames})
#     message(STATUS "${_variableName}=${${_variableName}}")
# endforeach()
