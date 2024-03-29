cmake_minimum_required(VERSION 3.5)
project(uavf_ros2_msgs)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()


# message generation
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)


set(msg_files
  "msg/GpsAltitudePosition.msg"
  "msg/NedEnuSetpoint.msg"
  "msg/NedEnuOdometry.msg"
  "msg/NedEnuWaypoint.msg"
)
set(srv_files
)
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  ${srv_files}
)
install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}
)
ament_export_dependencies(rosidl_default_runtime)

ament_package()
