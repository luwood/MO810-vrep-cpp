
set (VREP_PATH
    $ENV{VREP_PATH}
    CACHE "The VRep build path" STRING)

set (SOURCES  Robot.cpp Simulator.cpp 
    ${VREP_PATH}/programming/remoteApi/extApi.c
    ${VREP_PATH}/programming/remoteApi/extApiPlatform.c)

set (EXTRA_LIBRARIES pthread)
include_directories (${VREP_PATH}/remoteApi ${VREP_PATH}/include)

add_definitions( -Dpthread )
add_definitions (-DNON_MATLAB_PARSING)
add_definitions (-DMAX_EXT_API_CONNECTIONS=255)

SET(CMAKE_INCLUDE_CURRENT_DIR ON)

include_directories(${VREP_PATH}/programming/remoteApi/)
include_directories(${VREP_PATH}/programming/include/)
link_directories(${VREP_PATH})

add_library (VREPClient SHARED ${SOURCES})
add_executable(cli Main.cpp ${SOURCES})
target_link_libraries (cli VREPClient ${EXTRA_LIBRARIES})
