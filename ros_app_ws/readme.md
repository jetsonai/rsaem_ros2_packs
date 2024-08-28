# ROS YOLO Node

## 구독자 노드에 다름 함수를 포함하여 DetTopicSubscriber Class 를 구현하세요.

    def subscribe_detinfo(self, msg):
        self.get_logger().info(" label:{} cx:{} cy:{} bw:{} bh:{}'.format(msg.label,
                msg.center_x, msg.center_y, msg.b_width, msg.b_height)) 
