cmake_minimum_required(VERSION 3.8)
project(my_cpp_pkg)

# Find dependencies 
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED) 

# 3️ Executables
add_executable(talker src/publisher_node.cpp)
ament_target_dependencies(talker rclcpp std_msgs)

add_executable(listener src/subscriber_node.cpp)
ament_target_dependencies(listener rclcpp std_msgs)

# 4️ Install
install(TARGETS
  talker
  listener
  DESTINATION lib/${PROJECT_NAME})

# 5️ Testing
if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_copyright_FOUND TRUE)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()

