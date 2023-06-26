

如果机器人可以在N维空间中朝任意方向移动，则对于N维空间是完整性的。
非完整性约束：可控自由度小于机器人总自由度。
车辆可控自由度为2，包括油门/刹车和方向盘转角，难以满足任何方向的形式（除非发生打滑或者侧滑），所以是非完整性约束
完整性约束：总自由度等于可控自由度。

http://www.lxway.com/299525211.htm
程序注册twice:
source ./devel/setup.bash
rosrun beginner_tutorials talker 
New Terminal -->    source ./devel/setup.bash
rosrun beginner_tutorials listener



本文建立的是一个非常简单的发布（Publisher）、订阅(Subscriber)程序。
1、创建一个工作区（workspace）
工作区可以作为一个独立的项目进行编译，存放ROS程序的源文件、编译文件和执行文件。建立工作区的方法如下：

$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
$ catkin_init_workspace
虽然这时候工作区是空的，但是我们依然可以进行编译：

$ cd ~/catkin_ws/
$ catkin_make

这时候，会在当前文件夹下生成devel，build这两个子文件夹，在devel文件夹下能看到几个setup.*sh文件。

接下来把工作区在bash中注册

$ source devel/setup.bash

要验证是否已经在bash中注册可以使用如下命令：

$ echo $ROS_PACKAGE_PATH
/home/youruser/catkin_ws/src:/opt/ros/indigo/share:/opt/ros/indigo/stacks
如果能看到自己工作区的文件路径就说明已经成功了。


2、创建一个ROS工程包（Package）
在一个工作区内，可能会包含多个ROS工程包。而最基本ROS工程包中会包括CmakeLists.txt和Package.xml这两个文件，其中Package.xml中主要包含本项目信息和各种依赖（depends），而CmakeLists.txt中包含了如何编译和安装代码的信息。

首先切换到工作区：

$ cd ~/catkin_ws/src

现在可以使用catkin_create_pkg命令去创建一个叫beginner_tutorials的包，这个包依靠std_msgs、roscpp、rospy。

$ catkin_create_pkg beginner_tutorials std_msgs rospy roscpp

接下来在工作区编译这个工程包。

$ cd ~/catkin_ws
$ catkin_make



3、一个简单的发布（Publisher）、订阅(Subscriber)程序
3.1写一个发布（Publisher）节点

节点（node）是连接到ROS网络中可执行的基本单元。我们在这创建一个发布者---“talker”节点，这个节点持续对外发布消息。

首先我们要把目录切换到我们的beginner_tutorials工程包中

$ cd ~/catkin_ws/src/beginner_tutorials

因为我们已经编译过这个工程包了，所以会在beginner_tutorials文件夹下看到CmakeList.txt、package.xml文件和include、src这两个目录。接下来进入src子目录

$ cd src

在src目录中创建一个talker.cpp文件，里面的内容如下：

#include "ros/ros.h"
#include "std_msgs/String.h"

#include <sstream>
int main(int argc, char** argv)
{
  /*
   * The ros::init() function needs to see argc and argv so that it can perform
   * any ROS arguments and name remapping that were provided at the command line. For programmatic
   * remappings you can use a different version of init() which takes remappings
   * directly, but for most command-line programs, passing argc and argv is the easiest
   * way to do it.  The third argument to init() is the name of the node.
   *
   * You must call one of the versions of ros::init() before using any other
   * part of the ROS system.
   */
  ros::init(argc, argv, "talker");

  /*
   * NodeHandle is the main access point to communications with the ROS system.
   * The first NodeHandle constructed will fully initialize this node, and the last
   * NodeHandle destructed will close down the node.
   */
  ros::NodeHandle n;

  /*
   * The advertise() function is how you tell ROS that you want to
   * publish on a given topic name. This invokes a call to the ROS
   * master node, which keeps a registry of who is publishing and who
   * is subscribing. After this advertise() call is made, the master
   * node will notify anyone who is trying to subscribe to this topic name,
   * and they will in turn negotiate a peer-to-peer connection with this
   * node.  advertise() returns a Publisher object which allows you to
   * publish messages on that topic through a call to publish().  Once
   * all copies of the returned Publisher object are destroyed, the topic
   * will be automatically unadvertised.
   *
   * The second parameter to advertise() is the size of the message queue
   * used for publishing messages.  If messages are published more quickly
   * than we can send them, the number here specifies how many messages to
   * buffer up before throwing some away.
   */
  ros::Publisher chatter_pub = n.advertise<std_msgs::String>("chatter", 1000);

  ros::Rate loop_rate(10);

  /*
   * A count of how many messages we have sent. This is used to create
   * a unique string for each message.
   */
  int count = 0;
  while (ros::ok())
  {
    /*
     * This is a message object. You stuff it with data, and then publish it.
     */
    std_msgs::String msg;

    std::stringstream ss;
    ss << "hello world " << count;
    msg.data = ss.str();

    ROS_INFO("%s", msg.data.c_str());

    /*
     * The publish() function is how you send messages. The parameter
     * is the message object. The type of this object must agree with the type
     * given as a template parameter to the advertise<>() call, as was done
     * in the constructor above.
     */
    chatter_pub.publish(msg);

    ros::spinOnce();

    loop_rate.sleep();
    ++count;
  }


  return 0;
}

3.2写一个订阅（Subscriber）节点
还是在src目录下，创建一个listener.cpp文件。内容如下：

#include "ros/ros.h"
#include "std_msgs/String.h"

/*
 * This tutorial demonstrates simple receipt of messages over the ROS system.
 */
void chatterCallback(const std_msgs::String::ConstPtr& msg)
{
  ROS_INFO("I heard: [%s]", msg->data.c_str());
}

int main(int argc, char** argv)
{
  /*
   * The ros::init() function needs to see argc and argv so that it can perform
   * any ROS arguments and name remapping that were provided at the command line. For programmatic
   * remappings you can use a different version of init() which takes remappings
   * directly, but for most command-line programs, passing argc and argv is the easiest
   * way to do it.  The third argument to init() is the name of the node.
   *
   * You must call one of the versions of ros::init() before using any other
   * part of the ROS system.
   */
  ros::init(argc, argv, "listener");

  /*
   * NodeHandle is the main access point to communications with the ROS system.
   * The first NodeHandle constructed will fully initialize this node, and the last
   * NodeHandle destructed will close down the node.
   */
  ros::NodeHandle n;

  /*
   * The subscribe() call is how you tell ROS that you want to receive messages
   * on a given topic.  This invokes a call to the ROS
   * master node, which keeps a registry of who is publishing and who
   * is subscribing.  Messages are passed to a callback function, here
   * called chatterCallback.  subscribe() returns a Subscriber object that you
   * must hold on to until you want to unsubscribe.  When all copies of the Subscriber
   * object go out of scope, this callback will automatically be unsubscribed from
   * this topic.
   *
   * The second parameter to the subscribe() function is the size of the message
   * queue.  If messages are arriving faster than they are being processed, this
   * is the number of messages that will be buffered up before beginning to throw
   * away the oldest ones.
   */
  ros::Subscriber sub = n.subscribe("chatter", 1000, chatterCallback);

  /*
   * ros::spin() will enter a loop, pumping callbacks.  With this version, all
   * callbacks will be called from within this thread (the main one).  ros::spin()
   * will exit when Ctrl-C is pressed, or the node is shutdown by the master.
   */
  ros::spin();

  return 0;
}


3.3 编译创建的节点
在编译我们创建的节点之前，我们还需要编辑Cmakelist.txt文件（注意：是beginner_tutorials项目包下的CMakelist文件），告诉编辑器我们需要编辑什么文件，需要什么依赖。

$ gedit CMakeLists.txt

在文件末尾添加如下语句：

include_directories(include ${catkin_INCLUDE_DIRS})

add_executable(talker src/talker.cpp)
target_link_libraries(talker ${catkin_LIBRARIES})
add_dependencies(talker beginner_tutorials_generate_messages_cpp)

add_executable(listener src/listener.cpp)
target_link_libraries(listener ${catkin_LIBRARIES})
add_dependencies(listener beginner_tutorials_generate_messages_cpp)


将目录切换到工作区目录，并执行catkin_make运行命令：

$ cd ~/catkin_ws
$ catkin_make


不出意外的话，会出现如下界面：

ROS学习笔记

至此，程序已经创建完成，而接下来我们要检查一下我们创建的程序是否正确。



4、测试程序的正确性
首先，我们得要启动ROS核心程序roscore。

$ roscore


在使用我们的程序之前，需要先把程序注册

$ cd ~/catkin_ws
$ source ./devel/setup.bash


运行talker节点：

$ rosrun beginner_tutorials talker 


这时候会看到如下信息：

[INFO] [WallTime: 1314931831.774057] hello world 1314931831.77
[INFO] [WallTime: 1314931832.775497] hello world 1314931832.77
[INFO] [WallTime: 1314931833.778937] hello world 1314931833.78
[INFO] [WallTime: 1314931834.782059] hello world 1314931834.78
[INFO] [WallTime: 1314931835.784853] hello world 1314931835.78
[INFO] [WallTime: 1314931836.788106] hello world 1314931836.79

这就表示发布（Publisher）节点已经正确的运行了。

接下来运行listener节点：

$ rosrun beginner_tutorials listener


这时候会看到如下信息：

[INFO] [WallTime: 1314931969.258941] /listener_17657_1314931968795I heard hello world 1314931969.26
[INFO] [WallTime: 1314931970.262246] /listener_17657_1314931968795I heard hello world 1314931970.26
[INFO] [WallTime: 1314931971.266348] /listener_17657_1314931968795I heard hello world 1314931971.26
[INFO] [WallTime: 1314931972.270429] /listener_17657_1314931968795I heard hello world 1314931972.27
[INFO] [WallTime: 1314931973.274382] /listener_17657_1314931968795I heard hello world 1314931973.27
[INFO] [WallTime: 1314931974.277694] /listener_17657_1314931968795I heard hello world 1314931974.28
[INFO] [WallTime: 1314931975.283708] /listener_17657_1314931968795I heard hello world 1314931975.28

这说明订阅节点（listener）已经成功的接收到了发布节点（talker）发布的信息。至此，整个程序结束！





http://wiki.ros.org/apriltags_ros
https://github.com/RIVeR-Lab/apriltags_ros











