project(Localization)
<<<<<<< HEAD
set(CMAKE_CXX_STANDARD 14)
=======
set(CMAKE_CXX_STANDARD 17)
>>>>>>> b68b0fbb3d9e0478e56b9735f126d9d41cf657c4
set(CMAKE_CXX_STANDARD_REQUIRED ON)

cmake_minimum_required (VERSION 3.10)

# -g allows for gdb debugging
# turn on -03 for best performance
<<<<<<< HEAD
add_definitions(-std=c++14 -O3)

set(CXX_FLAGS "-pthread -fPIC -DNDEBUG -Wextra")
set(CMAKE_CXX_FLAGS "${CXX_FLAGS} -Wl,-Bstatic -lboost_filesystem -Wl,-Bdynamic")
=======
add_definitions(-O3)

#set(CXX_FLAGS "-pthread -fPIC -DNDEBUG -Wextra")
#set(CMAKE_CXX_FLAGS "${CXX_FLAGS} -Wl,-Bstatic -lboost_filesystem -Wl,-Bdynamic")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread -fPIC -DNDEBUG -Wextra")
>>>>>>> b68b0fbb3d9e0478e56b9735f126d9d41cf657c4

set(sources sm2-main.cpp helper.cpp)

find_package(PCL 1.2 REQUIRED)

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

if(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")

endif(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")

add_executable(scan_matching_2 ${sources} )

target_link_libraries(scan_matching_2 ${PCL_LIBRARIES} )
