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