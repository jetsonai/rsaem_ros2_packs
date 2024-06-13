# sensor_test_pack

ros2 launch hls_lfcd_lds_driver hlds_laser.launch.py

colcon build --packages-select sensor_test_pack

ros2 run sensor_test_pack lidar_sub_node 

=====================================================

# SLAM Navigation 실습

# 1. rsaem_ros_packs for ROBOT

### 1-1 빌드 (소스 전달 후)

cd rsaem_ws

colcon build

--------------------------------------

## 1-2 LAUNCH

### rsaembot_launch

export LIDAR_MODEL=LDS-01

(export LIDAR_MODEL 은 bashrc 에 있기 때문에 입력하지 않아도 됩니다)

ros2 launch rsaem_node rsaembot_launch.py

### teleop (다른 창)

ros2 run rsaem_teleop teleop_keyboard

### rviz2 확인 (다른 참)

ros2 launch rsaem_bringup rviz2_rsaem.launch.py

===========================================

### 로봇의 IP를 확인해주세요.

ifconfig

=====================================================

# 2. rsaem_ros_packs for PC

### 주의) 이제 PC 에서만 명령을 내리게 됩니다.

## 2-1 PC 환경 세팅

### bashrc 수정

ROS_DOMAIN_ID 를 로봇에 세팅해주신 본인 ID 로 수정해주세요

===========================================

## 2-2 PC 빌드 (소스 전달 후)

cd rsaem_ws

colcon build

==================================

## 2-3 BRINGUP R-SAEM BOT

### brigup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99

ros2 launch rsaem_bringup rsaem.launch.py

### teleop (다른 창)

ros2 run rsaem_teleop teleop_keyboard

### 동작을 확인해주세요

============================================

## 2-4 원격 제어

### brigup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99
 
ros2 launch rsaem_bringup rsaem.launch.py

### teleop (다른 창)

ros2 run rsaem_teleop teleop_keyboard

* 모든 창을 닫아주세요

============================================

## 2-5 SLAM 실습

### 팬스를 설치해주세요. 로봇 시작 위치와 방향을 기억해주세요.

### brigup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99
 
ros2 launch rsaem_bringup rsaem.launch.py

###  cartographer (다른 창)

ros2 launch rsaem_cartographer cartographer.launch.py

### teleop (다른 창)

ros2 run rsaem_teleop teleop_keyboard

### -->  teleop 을 이용하여 맵을 완성합니다. 검은 색 테두리으로 폐쇄 공간이 될 수 있도록 해주십시오.

### map 저장 (다른 창)

ros2 run nav2_map_server map_saver_cli -f ~/map

### --> 저장 후 모든 창을 닫아주세요

============================================

## 2-6 Navi2 실습

### SLAM 때 사용한 처음 위치와 방향에 위치시켜주세요.

### brigup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99

ros2 launch rsaem_bringup rsaem.launch.py

### navi2 (다른 창)

ros2 launch rsaem_navigation2 navigation2.launch.py map:=$HOME/map.yaml

========================================

