# Discrete Bayes Filter for Localization

This is a simplified bayes filter for localization. We have a robot which has the full information of the map (which looks like a face). Each yellow point means there is metal in that possition. The robot has a faulty metal detector and a faulty actuators meaning. It detects correctly if there are any metals in the current possition 0.8 of the times. And the robot fails to moves 10% of the times.

Bayes filter is based on two simple equations. First the prediction of the position given the information it has and Bayes' rule. Which is

![1](imgs/1.png)

And second, the correction of that prediction (which is made using the probability of finding that measurement given the position in we think we are)

![2](imgs/2.png)

## Results

This is the result over 200 episodes, as we can see given this maps, it works very good. Some times it gets lost but that is because the map has a lot of similar spots.

The first image (top right) it the ground-truth map and the real position of the robot. The image to the right is where the robot think it is given an action (the more yellowish, more probable it is there). The Likelihood image is the probability of making a measurement give the possition. The top-right image is the posterior belief of the position given a certain measure (i.e. after measuring the current position)

The bottom left image shows the real position of the robot (yellow), the most probable position where the robot thinks he is (yellow 90%) and the prior (yellow 50% or closer to blue than yellow).

Finally the bottom-right image is the error between the real position and the predicted position (the lower the better)

![working](imgs/gif_compressed.gif)

## Useful tools

### Create gif

The default algorithm saves the imgs in the folder `img` in the root folder, from the `img` folder run

`convert -delay 20 -loop 0 *.png myimage.gif` 

to create the gif. Probable you will need to install to run first 

`sudo apt-get install imagemagick`

### Additional information

The original unsolved environment is 
`https://github.com/ipab-rad/DMR_SEARCH`
