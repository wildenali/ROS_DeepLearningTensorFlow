# ROS_DeepLearningTensorFlow

## Create Own ROS Package that Recognises Images with TensorFlow

Goal:
- Setup catkin_ws to use python3
- Use a TensorFlow 2.0 Model that has learned hundreds of images

### Setup catkin_ws to use python3
1. Setup the Python3 ROS catkin_ws environment
    ```sh
    $ cd ~/catkin_ws/src/ROS_DeepLearningTensorFlow
    $ mkdir -p my_catkin_ws_python3/src
    $ cd ~/catkin_ws/src/ROS_DeepLearningTensorFlow/my_catkin_ws_python3
    $ source ~/.py3venv/bin/activate
    $ source /home/user/.catkin_ws_python3/devel/setup.bash
    $ catkin_make -DPYTHON_EXECUTABLE:FILEPATH=/home/user/.py3venv/bin/python
    $ source devel/setup.bash
    $ rospack profile
    ```


2. Create the ROS package for this course
    ```sh
    $ source ~/.py3venv/bin/activate
    $ cd ~/catkin_ws/src/ROS_DeepLearningTensorFlow/my_catkin_ws_python3/src
    $ catkin_create_pkg my_tf_course_pkg rospy std_msgs sensor_msgs
    $ cd ..;source devel/setup.bash;rospack profile
    $ roscd my_tf_course_pkg;mkdir launch;mkdir scripts
    ```

3. This is recommended each time that you start a new webshell ( compiling is not necessary if done previously)
    ```sh
    $ cd ~/catkin_ws/src/ROS_DeepLearningTensorFlow/my_catkin_ws_python3
    $ source ~/.py3venv/bin/activate
    $ source /home/user/.catkin_ws_python3/devel/setup.bash
    $ catkin_make -DPYTHON_EXECUTABLE:FILEPATH=/home/user/.py3venv/bin/python
    $ source devel/setup.bash
    $ rospack profile
    ```

### Create TensorFlow Scripts
1. Now going to create two python scripts that will retrieve the image data, classify it based on a downloaded TensorFlow model, and publish the results into a ROS topic.
    - Retrieve ROS image from a topic and sending them to a classification class that will decide which objects are present on the scene
        ```sh
        $ roscd my_tf_course_pkg;cd scripts
        $ touch search_for_mira_robot.py
        $ chmod +x search_for_mira_robot.py
        ```