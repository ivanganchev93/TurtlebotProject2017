# TurtlebotProject2017

### Description:
This is my 4th year project as part of my degree in computing science and physics. The application allows for a Kobuki Turtlebot to 
1. Create a 2D map of its environment, which could be used to localise objects; 
2. Recognise objects using Google Vision and store their location on the map;
3. Use the map and object localisation to autonomously navigate to any area in the map.
It was developed to allow University of Glasgow staff to use the robot to deliver objects between office with minimal effort. 

### How to run application:
  !!! Important - Application runs on Linux 14.04
   
-Have all ROS dependecies installed for the Turtlebot by following the kobuki installation instructions on http://wiki.ros.org/Robots/TurtleBot

- Clone the repository

Steps:

 1. To ﬁrst initialise the turtlebot on a terminal ”roslaunch turtlebot bringup minimal.launch” needs to be executed. This will start the neccessary nodes for the other applications to run. 
 2. On a new terminal run ”roslaunch botty mapping botty mapping.launch”. This starts the 3d sensor of the robot and the gmapping package.
 3. On a 3 separate terminals run concevutively ”rosrun botty mapping mapping.py”, ”rosrun botty mapping control.py” and ”rosrun botty detect vision.py”. The ﬁrst two make the robot move autonomously and build the map while the third node creates the list of objects in the environment. 
 4. (optional) On a separate terminal run ”roslaunch turtlebot rviz launchers view navigation.launch”. This willvisualise themap that isbeingbuilt. Once agood enough maphasbeenbuilttheterminalsfrom point 2,3 and 4 can be stopped. 
 5. On a new terminal run ”rosrun map server map saver [location to save map/name of map]. This saves the built map on a speciﬁed location.
 6. Move the map ﬁles into the botty/maps/mymap folder and name them mymap. 
 7. Move the items detected.txt that was created in the maps folder form the mapping module inside the mymap folder. 
 8. Open the mymap.pmg ﬁle and check its pixel dimensions. It will be used to for generating the real world dimensions of the map. 
 9. Open the mymap.yaml ﬁle and check the pixel resolution information (should be 0.05). 
 10. Go to the stage folder and open the .world ﬁle. 
 11. Edit on the ﬂoorplan the size information. The ﬁrst value is the x pixel resolution*resolution from the .yaml ﬁle and the second is the y pixel resolution*resolution. 
 12. On the pose information of the ﬂoorplan put half of the size values, respectively. 
 13. On the turtlebot pose information enter the same values as the ones from point 12.
 14. Now you can run the Navigation module by opening a terminal and runnung ”roslaunchturtlebot navigation amcl demo.launchmap ﬁle:=/your path/your map.yaml”andonanotherterminal”rosrunbotty navigation map navigation.py.
 15. Choose a destination from the list and the turtlebot should move to that position on the map.
