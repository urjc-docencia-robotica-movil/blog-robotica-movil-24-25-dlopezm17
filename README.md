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
