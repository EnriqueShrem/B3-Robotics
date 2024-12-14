# Robot Design & CAD
The robot design has been defined analytically, considering the real applications for which was developed. 

Kinematics:
Joints:
- Joint 0: fixed.
- Joint 1: revolute.
- Joint 2: revolute.
- Joint 3: revolute.
- Joint 4: revolute.
- Joint 5: prismatic

Links:
- Link 0 (base link): the base link does not add any limitation for the robot movement, but contributes to the vertical (z axis of base) range.
- Link 1: contributes to the range and allows movement normal and away from the base z axis direction.
- Link 2: Allows the movement towards the base for which as large as the link 1 would be optimal.
- Link 3: The link rotates holding link 4 and limiting its motion.
- Link 4: allows and sets the maximun range at the vertical direction.


Isometric
<p align="center">
  <img src="../Assets/isometric.jpeg" style="width:30%; height:30%;">
</p>
<p align="left">
  <img src="../Assets/top.jpeg" style="width:30%; height:30%;">
</p>
<p align="left">
  <img src="../Assets/front.jpeg" style="width:30%; height:30%;">
</p>
<p align="left">
  <img src="../Assets/side.jpeg" style="width:10%; height:10%;">
</p>
