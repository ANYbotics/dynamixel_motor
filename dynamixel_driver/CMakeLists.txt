# http://ros.org/doc/groovy/api/catkin/html/user_guide/supposed.html
cmake_minimum_required(VERSION 3.5.1)
project(dynamixel_driver)

find_package(catkin REQUIRED)

catkin_python_setup()

catkin_package(
    CATKIN_DEPENDS rospy diagnostic_msgs
)

# Testing
if(CATKIN_ENABLE_TESTING)
  find_package(cmake_python_coverage REQUIRED)
  if(cmake_python_coverage_FOUND)
    add_pytest_with_coverage(test/test_empty.py dynamixel_driver)
  endif()
endif()

install(PROGRAMS
  scripts/change_id.py
  scripts/info_dump.py
  scripts/set_servo_config.py
  scripts/set_torque.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
