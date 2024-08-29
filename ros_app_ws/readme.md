# ROS YOLO Node

# simple 버전 노드

ros2 run ros_yolo_pack ros_yolo_node

# 발행자 노드

ros2 run ros_yolo_pack ros_yolo_test_pub

## 구독자 노드에 다음 함수를 포함하여 DetTopicSubscriber Class 를 구현하세요.

    def subscribe_detinfo(self, msg):
        self.get_logger().info(" label:{} cx:{} cy:{} bw:{} bh:{}'.format(msg.label,
                msg.center_x, msg.center_y, msg.b_width, msg.b_height)) 

colcon build --packages-select ros_yolo_pack

ros2 run ros_yolo_pack ros_yolo_teset_sub

