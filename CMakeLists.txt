cmake_minimum_required(VERSION 2.8)
project(pose_viewer)

# Dependencies
find_package(Eigen3 3.3.8 EXACT REQUIRED PATHS ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/eigen/share/eigen3/cmake)
if(${Eigen3_FOUND})
    message(STATUS "Found: Eigen3 - ${EIGEN3_INCLUDE_DIRS}")

    include_directories(${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/eigen/include/eigen3)
    set(EIGEN3_LIBS Eigen3::Eigen)
endif(${Eigen3_FOUND})

find_package(Pangolin 0.8 EXACT REQUIRED PATHS ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/pangolin/lib/cmake/Pangolin)
if (${Pangolin_FOUND})
    message(STATUS "Found Pangolin - ${Pangolin_DIR}")

    include_directories(${Pangolin_INCLUDE_DIRS})
    set(PANGOLIN_LIBS ${Pangolin_LIBRARIES})

else (${Pangolin_FOUND})
    message(STATUS "Could not support Pangolin")
endif (${Pangolin_FOUND})

# Executable
add_executable(pose_viewer examples/pose_viewer.cpp)
target_link_libraries(pose_viewer ${Pangolin_LIBRARIES})
