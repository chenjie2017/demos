cmake_minimum_required(VERSION 3.5)

project(dummy_map_server)

if(NOT WIN32)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -Wall -Wextra -Wpedantic")
endif()

find_package(ament_cmake REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rmw REQUIRED)

add_executable(dummy_map_server src/dummy_map_server.cpp)
ament_target_dependencies(dummy_map_server
  "rclcpp"
  "nav_msgs")
install(TARGETS dummy_map_server
  DESTINATION bin)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
