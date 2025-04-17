# RSaem ROS2 Packages

8.6.1	rsaem_ros_packs for ROBOT

##	환경 확인

bashrc 에 rsaem_ws setup.bash 실행 추가 (한번만)

echo "source ~/rsaem_ws/install/setup.bash" >> ~/.bashrc

echo "export LIDAR_MODEL=LDS-01" >> ~/.bashrc

source ~/.bashrc

## 	Robot Teleop (Local)

* rsaembot_launch

export LIDAR_MODEL=LDS-01

* export LIDAR_MODEL 은 bashrc 에 있기 때문에 입력하지 않아도 됩니다
* 
ros2 launch rsaem_bringup rsaem.launch.py

## teleop (다른 창) (종이컵 이용 필수)

ros2 run rsaem_teleop teleop_keyboard

종이컵 위에서 바퀴가 움직이는지 확인해주세요
로컬에서 로봇 토픽과 연결 관계 확인 (다른 참)

ros2 topic list

rqt_graph

## 로컬에서 rviz2 확인 (다른 참)

ros2 launch rsaem_bringup rviz2_rsaem.launch.py

rviz 상의 노드들과 TF 들을 확인해주세요

#	rsaem_ros_packs for PC 

다운로드 받아서 압축을 풀어주세요

https://drive.google.com/file/d/198EhlmS0NeUgq0NHCpdXkJo6aTuB2b4W/view?usp=sharing


로봇의 IP를 확인해주세요.

ifconfig

원격 테스트를 위해 로봇의 터미널창을 모두 닫아주십시오 (필수)

주의) 이제 PC 에서만 명령을 내리게 됩니다.

##	PC 환경 세팅

bashrc 수정 (한번만)

* ROS_DOMAIN_ID 를 로봇에 세팅해주신 본인 ID 로 수정해주세요
  
cd

gedit .bashrc

수정(export ROS_DOMAIN_ID=30) -> 저장 -> 창 끄기

##	PC 환경

cd rsaem_ws

colcon build

bashrc 에 rsaem_ws setup.bash 실행 추가 (한번만)

echo "source ~/rsaem_ws/install/setup.bash" >> ~/.bashrc

echo "export LIDAR_MODEL=LDS-01" >> ~/.bashrc

source ~/.bashrc

#	BRINGUP R-SAEM BOT

bringup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99

# 여기서부터는 로봇에 연결된 터미널 화면

ros2 launch rsaem_bringup rsaem.launch.py

원격에서 로봇 토픽과 연결 관계 확인 (다른 참)

ros2 topic list

rqt_graph

원격 rviz2 확인 (다른 참)

ros2 launch rsaem_bringup rviz2_rsaem.launch.py

#	BRINGUP & 원격 제어

bringup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99

# 여기서부터는 로봇에 연결된 터미널 화면

ros2 launch rsaem_bringup rsaem.launch.py

teleop (다른 창)
ros2 run rsaem_teleop teleop_keyboard

동작 여부를 확인 한 후 케이블을 뽑고 바닥에서 젼진 후진 좌회전 우회전 등 동작을 확인해주세요
모든 창을 닫아주세요

8.6.2.5	SLAM 실습
팬스를 설치해주세요. 로봇 시작 위치와 방향을 기억해주세요.
bringup (원격 접속)
ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99

# 여기서부터는 로봇에 연결된 터미널 화면

ros2 launch rsaem_bringup rsaem.launch.py

cartographer (다른 창)

ros2 launch rsaem_cartographer cartographer.launch.py

teleop (다른 창)

ros2 run rsaem_teleop teleop_keyboard

--> teleop 을 이용하여 맵을 완성합니다. 검은 색 테두리으로 폐쇄 공간이 될 수 있도록 해주십시오.

map 저장 (다른 창)

ros2 run nav2_map_server map_saver_cli -f ~/map2

--> 저장 후 모든 창을 닫아주세요

8.6.2.6	Navi2 실습

SLAM 때 사용한 처음 위치와 방향에 위치시켜주세요.

bringup (원격 접속)

ssh nvidia@{MY_RSAEM BOT} 예 ) ssh nvidia@192.168.100.99

# 여기서부터는 로봇에 연결된 터미널 화면
ros2 launch rsaem_bringup rsaem.launch.py

navi2 (다른 창)
ros2 launch rsaem_navigation2 navigation2.launch.py map:=$HOME/map2.yaml

