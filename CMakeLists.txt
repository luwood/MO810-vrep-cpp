project (VREPClient)
cmake_minimum_required(VERSION 2.8)

set (CMAKE_CXX_STANDARD 11)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set (VREP_PATH
    $ENV{VREP_PATH}
    CACHE "The VRep build path" STRING)

set (MSOURCES  src/Robot.cpp src/Simulator.cpp 
    ${VREP_PATH}/programming/remoteApi/extApi.c
    ${VREP_PATH}/programming/remoteApi/extApiPlatform.c)

set (EXTRA_LIBRARIES pthread)
include_directories (${VREP_PATH}/remoteApi ${VREP_PATH}/include)

add_definitions( -Dpthread )
add_definitions (-DNON_MATLAB_PARSING)
add_definitions (-DMAX_EXT_API_CONNECTIONS=255)

include_directories(src/)
include_directories(${VREP_PATH}/programming/remoteApi/)
include_directories(${VREP_PATH}/programming/include/)
link_directories(${VREP_PATH})

add_library (VREPClient SHARED ${MSOURCES})
add_executable(cli src/Main.cpp ${MSOURCES})
target_link_libraries (cli VREPClient ${EXTRA_LIBRARIES})

