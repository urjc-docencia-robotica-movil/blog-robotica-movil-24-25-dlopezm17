Link to the execution video: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/EZa_0EGC0zZBrC4YgH5UgZoBFyd19ITwC57z4gGnNyYidw?e=aL0eeB&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D


**P2**


In this exercise the first thing I did was to create the image filter. I used HSV colors insted of RGB colors due to the facility to diferenciate between red and white.
Then I started the PID controller. Firstly, with a fixed linear speed I disigned the controller for the angular speed. When this was working, I did the linear speed one in order to finish the race quicker.
The I tryed to create a specific PID to the curves and one to the straight zones, but I founded that the robot was barely using the second one, so I eliminated it.
With the normal model working, I started the ackerman mode one, but I founded much harder than spected to create the controller, so at the end I decided to don't have a controller for the speed an go with a fixed one.

Video of the normal mode car: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/Eal-BON6vtFAuzkbZmdfDHcB4R6P8X35wd0bLjyIcLJM0w?e=Ej7bT5&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

Video of the ackerman mode car: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/Ecz6UjSCm7ZPkMarmCMuiJUB8WY_-Rf3RX6hjEV0rU5YjQ?e=nTzZYb&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D



**P3**

The program first takes the localitation of the objective and, if is close enough, mark it as checked and take the next one. Then it parse the laser data to create the repulsive vector. This is done by firstly changing the angle of the laset to have the x = 0 in the same position as the car have. Then it calculate the force by scaling the module first by using the function 5/(dist²) to increase exponentialy the force if the obstacle is getting closer and closer and then multipling it by (1+cos(angle))¹·⁵ to increase the importance to the obstacles in front of the robot. With the force I calculate the position and I add every data for each laser data and calculate the average. For the actractive vector I just take the coordenates, calculate the distance and the angle and the x, y coordenates would be the minimun between 4 and the distance (to not get enormous vectors) and multiply by the cos/sin respectively. Usin the two vectors I sum them together multiply by alpha and beta. The resultant force would be scaled and used to get the speed. If the vercor is in front of the car, the speed will ignore the y coordenate but, if not, both would be used. The speed is set to have at least an absolute value of 0.3 to avoid the situations in which the car is stucked between the atractive and repulsive vector.

*Problems*

Due to the rectangular shape of the car it could crash it's back without noticing it. 


Video: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/EWfslzSmUvZBowyU8SdqqjgBCgC74myvLIRlUxsLn4tcgA?e=nvO65z&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D




**P4**

This program is divided in to parts, to calculate the plan and to navigate. Fistly, the code must decide in which mode is in. To do so, it checks it's objetive. If the objetive is different to the one in the previous itertion, it would create a gradient path plan to reach the objetive and, if the objetive is the same that it previously had, the car would navigate to the objetive.

If the robot is in the create plan mode, it would use a BFS algorithm to calculate the cost that it would have in reality to reach the objetive. That is done by putting in a queue the objetive position and calculating the posible next cells of the map in which the robot can be. Then it adds a cost, that is the cost that the previous node had plus the distance betwwen this new position and the one of the previous node. This way the cost is related to the distance that the car have to travel by the shortest route posible. If it would had been the real distance between the point and the objetive, the car could find local minimums for where it won't be able to scape. The gradient path would just calculate a bit more than the nodes expanded when it finds the position of the car. This way it don't calculate the whole map, something that takes a long time but have a little margin to help the car find the initial direction. Onces the gradient plan is finished, it would calculate, if it hadn't been calculated before, a plan that contains a cost for the areas next to the walls. This would aboid the car going next to the walls. When both plans are finished, the definitive one would be the sum of both plans.

While in the navigation mode, the robot would check the cost of the cells surrounding it and would go in the direction of the one with the less cost. When it finds it, ti would convert the coordenades to other relative to the car's position and would be used as the speed the car have to use to reach the objetive.


*Problems*

The algorithim that caluclates the map was extremely time consuming so I had to limit the number of times the map was shown in the screen to make it much faster.

Sometimes if the car was far away from the objetive, the amount of nodes that it needed was high, and if that number was used when the car was close it expanded too much, so I used a variable amount of extra nodes to fix it.

Video:


