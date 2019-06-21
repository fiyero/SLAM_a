# Graph SLAM for landmark detection and tracking
## https://medium.com/@patrickhk/graph-slam-for-landmark-detection-and-tracking-49f270e47c2a

### Define a robot class
First we have to define a robot class and visualize the robot in a 2D world. Since movement and measurement both have uncertainty, we add motion noise and measurement noise in the motion and sense function.

The initial pose for the robot was (5,5) in the x,y coordinate.<br/>
![p1](https://cdn-images-1.medium.com/max/800/1*luJCbUMoOUNXrfVLot4Xqg.png)<br/>
After movement of (1,1), the new pose is (5.81287, 5.91232) instead of (6,6) due to uncertainty.<br/>
![p2](https://cdn-images-1.medium.com/max/800/1*u4aSK2QpSpYxjFwyRupovg.png)<br/>

### Implement constraints Omega and Xi
This is a 2D world so each pose and landmark have x and y component<br/>

![p3](https://cdn-images-1.medium.com/max/800/1*OMZfaWkInj42JII8CN50IA.png)<br/>
In the project I use 20 timesteps and 5 landmark locations so I will have 50 constraints and initialize the Omega as a (50,50) matrix with all 0 values.<br/>

Xi will be a row vector of (50,)<br/>

I set the world size as 100 and we assume the robot’s starting position is in the middle of the world with 0 uncertainty. Therefore starting pose is (world_size/2,world_size/2) = (50,50)<br/>
### Implement Graph SLAM
We have to update the omega and Xi with motion and measurements data over timesteps. We can introduce variable called alpha and beta to represent the noise in motion and measurement. Remember this is 2D and we have to update in both x and y directions. This is the most challenging part of the project and it will be easier to consider in a simpler constraint example.<br/>

The whole point is to get the best estimate of poses and landmark positions from Omega_inverse * Xi<br/>
![p4](https://cdn-images-1.medium.com/max/800/1*uksj0RDUdRcG4Hmdh1kgQg.png)<br/>
### Visualize
As a result with updating the measurement and motion data, we can estimate where the robot is after considering the uncertainty factor.<br/>

![p6](https://cdn-images-1.medium.com/max/800/1*eQP8Bu8JpR672DRjzJyecw.png)<br/>

-------------------------------------------------------------------------------------------------------------------------------------
### More about me
[[:pencil:My Medium]](https://medium.com/@patrickhk)<br/>
[[:house_with_garden:My Website]](https://www.fiyeroleung.com/)<br/>
[[:space_invader:	My Github]](https://github.com/fiyero)<br/>
