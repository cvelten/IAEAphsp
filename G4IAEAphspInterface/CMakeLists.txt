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
set (IAEAPHSP_INCLUDE_DIR "${IAEAPHSP_INCLUDE_DIR}")
set (IAEAPHSP_LIBRARY_DIR "${IAEAPHSP_LIBRARY_DIR}")
include_directories(${IAEAPHSP_INCLUDE_DIR})
link_directories(${IAEAPHSP_LIBRARY_DIR})

# source files
file(GLOB sources ${PROJECT_SOURCE_DIR}/*.cc)
file(GLOB headers ${PROJECT_SOURCE_DIR}/*.hh)

# targets
add_library(G4IAEAphspInterface-static STATIC ${headers} ${sources})

add_library(G4IAEAphspInterface SHARED ${headers} ${sources})
target_link_libraries(G4IAEAphspInterface
	iaea_phsp
	${Geant4_LIBRARIES})