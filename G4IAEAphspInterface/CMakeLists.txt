cmake_minimum_required(VERSION 3.8)
if(${CMAKE_VERSION} VERSION_LESS 3.12)
	cmake_policy(VERSION ${CMAKE_MAJOR_VERSION}.${CMAKE_MINOR_VERSION})
endif()

project(G4IAEAphspInterface)

# Geant4
find_package(Geant4 REQUIRED)
include(${Geant4_USE_FILE})
include_directories(${PROJECT_SOURCE_DIR}/include)

# iaea_phsp
include_directories(${PROJECT_SOURCE_DIR}/../iaea_phsp)

file(GLOB sources ${PROJECT_SOURCE_DIR}/*.cc)
file(GLOB headers ${PROJECT_SOURCE_DIR}/*.hh)

add_library(G4IAEAphspInterface ${headers} ${sources})
