<<<<<<< HEAD
# --- CARLA PFADE ANPASSEN ---
# Ersetze 'alexander' durch deinen echten Usernamen, falls nötig
set(CARLA_ROOT /home/alexander/Carla) 

# Pfade zu den Header-Dateien (Includes)
include_directories(${CARLA_ROOT}/LibCarla/source)
include_directories(${CARLA_ROOT}/Build/boost-1.80.0-install/include) # Version prüfen!
include_directories(${CARLA_ROOT}/Build/rpclib-v2.2.1_c5-libstdcxx-install/include)

# Pfade zu den Bibliotheken (Libs)
# Wir suchen die .a Dateien direkt in deinem Carla-Build-Ordner
set(CARLA_LIB_DIR ${CARLA_ROOT}/Build/libcarla-client-build.release/LibCarla/cmake/client)
set(BOOST_LIB_DIR ${CARLA_ROOT}/Build/boost-1.80.0-install/lib) # Version prüfen!
set(RPC_LIB_DIR ${CARLA_ROOT}/Build/rpclib-v2.2.1_c5-libstdcxx-install/lib)

set(carla_libs 
    ${CARLA_LIB_DIR}/libcarla_client.a 
    ${BOOST_LIB_DIR}/libboost_filesystem.a
    ${BOOST_LIB_DIR}/libboost_system.a
    ${RPC_LIB_DIR}/librpc.a
    # Füge hier weitere .a Dateien hinzu, falls der Linker noch meckert
)
# --- ENDE ANPASSUNG ---

# Rest wie gehabt...
target_link_libraries(cloud_mapper ${PCL_LIBRARIES} ${carla_libs} pthread)
=======
project(Localization)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

cmake_minimum_required (VERSION 3.10)

# -g allows for gdb debugging
# turn on -03 for best performance
add_definitions(-std=c++14 -O3)

set(CXX_FLAGS "-pthread -fPIC -DNDEBUG -Wextra")
set(CMAKE_CXX_FLAGS "${CXX_FLAGS} -Wl,-Bstatic -lboost_filesystem -Wl,-Bdynamic")

set(sources map-main.cpp helper.cpp)

set(CARLALIB_DIR ${CMAKE_SOURCE_DIR}/libcarla-install/lib)
set(carla_libs  ${CARLALIB_DIR}/libboost_filesystem.a ${CARLALIB_DIR}/libboost_program_options.a ${CARLALIB_DIR}/libboost_python38.a ${CARLALIB_DIR}/libboost_system.a ${CARLALIB_DIR}/libcarla_client.a ${CARLALIB_DIR}/librpc.a ${CARLALIB_DIR}/libDebugUtils.a ${CARLALIB_DIR}/libDetour.a ${CARLALIB_DIR}/libDetourCrowd.a ${CARLALIB_DIR}/libDetourTileCache.a ${CARLALIB_DIR}/libRecast.a)

link_directories(libcarla-install/lib)
include_directories(libcarla-install/include)
include_directories(libcarla-install/include/system)
include_directories(rpclib/include)

find_package(PCL 1.2 REQUIRED)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

if(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")

endif(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")

add_executable(cloud_mapper ${sources} )

target_link_libraries(cloud_mapper ${PCL_LIBRARIES} ${carla_libs})
>>>>>>> b68b0fbb3d9e0478e56b9735f126d9d41cf657c4
