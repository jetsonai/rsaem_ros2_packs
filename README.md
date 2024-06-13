# sensor_test_pack

ros2 launch hls_lfcd_lds_driver hlds_laser.launch.py

colcon build --packages-select sensor_test_pack

ros2 run sensor_test_pack lidar_sub_node 


# rsaem_ros_packs

cd rsaem_ws

colcon build --packages-select rsaem_msgctl


source ~/rsaem_ws/install/setup.bash

colcon build --packages-select rsaem_node

colcon build --packages-select rsaem_teleop

colcon build --packages-select rsaem_cartographer

colcon build --packages-select rsaem_description

colcon build --packages-select rsaem_bringup

OR 

다 같이 빌드하기 위해서

colcon build

--------------------------------------

ros2 launch rsaem_node rsaembot_launch.py

ros2 run rsaem_teleop teleop_keyboard
---------------------

export LIDAR_MODEL=LDS-01

ros2 launch rsaem_bringup rsaem.launch.py


ros2 launch rsaem_bringup rviz2_rsaem.launch.py

----------------------------

============================================
ssh ubuntu@{IP_ADDRESS_OF_RASPBERRY_PI}
 
ros2 launch rsaem_bringup rsaem.launch.py

ros2 launch rsaem_cartographer cartographer.launch.py

ros2 run rsaem_teleop teleop_keyboard

ros2 run nav2_map_server map_saver_cli -f ~/map

================================================

ssh ubuntu@{IP_ADDRESS_OF_RASPBERRY_PI}

ros2 launch rsaem_bringup rsaem.launch.py

ros2 launch rsaem_navigation2 navigation2.launch.py map:=$HOME/map.yaml
