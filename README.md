Link to the execution video: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/EZa_0EGC0zZBrC4YgH5UgZoBFyd19ITwC57z4gGnNyYidw?e=aL0eeB&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D


**P2**


In this exercise the first thing I did was to create the image filter. I used HSV colors insted of RGB colors due to the facility to diferenciate between red and white.
Then I started the PID controller. Firstly, with a fixed linear speed I disigned the controller for the angular speed. When this was working, I did the linear speed one in order to finish the race quicker.
The I tryed to create a specific PID to the curves and one to the straight zones, but I founded that the robot was barely using the second one, so I eliminated it.
With the normal model working, I started the ackerman mode one, but I founded much harder than spected to create the controller, so at the end I decided to don't have a controller for the speed an go with a fixed one.

Video of the normal mode car: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/Eal-BON6vtFAuzkbZmdfDHcB4R6P8X35wd0bLjyIcLJM0w?e=Ej7bT5&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

Video of the ackerman mode car: https://urjc-my.sharepoint.com/:v:/g/personal/d_lopezm_2022_alumnos_urjc_es/Ecz6UjSCm7ZPkMarmCMuiJUB8WY_-Rf3RX6hjEV0rU5YjQ?e=nTzZYb&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D
