cmake_minimum_required(VERSION 3.8)
project(sambot_description)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)

# add_executable(talker src/publisher_member_function.cpp)
# ament_target_dependencies(talker rclcpp std_msgs)

# add_executable(listener src/subscriber_member_function.cpp)
# ament_target_dependencies(listener rclcpp std_msgs)

install(DIRECTORY
  launch urdf
  DESTINATION share/${PROJECT_NAME}
)
install(DIRECTORY
  params
  DESTINATION share/${PROJECT_NAME}
)

# add_executable(sambot_exe src/sambot_file.cpp)
# ament_target_dependencies(sambot_exe 
# rclcpp 
# std_msgs
# nav_msgs
# geometry_msgs
# sensor_msgs
# )

install(DIRECTORY 
  src rviz world
  DESTINATION share/${PROJECT_NAME}
  )

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
