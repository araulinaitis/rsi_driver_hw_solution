# rsi\_driver\_hw

Most companies are content with writing programs on robot controllers and letting the robots repeat those programs. However, our robots get bored quickly, so we always want to give them new paths from an external computer. 

To give the robots paths, we need to use two software packages:

The first is a Kuka package called RSI (Robot Sensor Interface). RSI lets us control the robots without having to write a program beforehand. Want the robot to do a sine wave? RSI. Want the robot to move based on a distance sensor? RSI.

The second is an RSI plugin called EthernetRSIXML. This plugin enables us to send data to the robots from an external PC. Now, we can make paths on the PC and send them to the robot. Currently, we run the robots in cartesian coordinates, giving them XYZ points in space to hit. Now, though, we're getting cocky, and think it's time to send them joint commands instead.

## Your Job

This is what you've (probably never) trained for. I have a program on my computer that can tell the robots what joints to move, but I haven't written any program to run on the robot controller, connect to the PC, and move the robots. I want you to write this program. A copy of it will live on each robot and talk to the computer.

### Specifications

The PC will send you this stuff:

- Joint Positions A1 - A6, E1  # (relative, deg & mm)

The PC needs to know this stuff:

- Joint Positions A1 - A6, E1  # encoder values (absolute, deg & mm)

- Joint Currents A1 - A6, E1   # controller currents (amps)

Thankfully, I've dredged up some documentation that should help you out. I squirreled it away as a bunch of PDFs in the `docs/` folder.

- `KUKA_Ethernet_RSI_XML_1_2_en.pdf`: This documentation is the meat and potatoes. Use it to learn about the RSI component for ethernet communication. It even has example code! (Check out `ERXDemo_1.src`)

- `Robot_Sensor_Interface_2_3_en.pdf`: Use this one to learn more about how RSI works.

- `KUKA_System_Software_5_6_en.pdf`: Use this to look up stuff about Kuka Robot Language. This manual is huge, and most of it isn't relevant. Don't spend too much time here.

Some of these documents have source code that comes with them. Don't get too excited, none of it solves your problem. Still, it might be useful. I put some of the files in the `examples/` folder.

## Submission

In order to submit the assignment, do the following:

1. Navigate to GitHub's project import page: [https://github.com/new/import](https://github.com/new/import)

2. In the box titled "Your old repository's clone URL", paste the homework repository's link: [https://github.com/Machina-Labs/path_analysis_hw](https://github.com/Machina-Labs/path_analysis_hw)

3. In the box titled "Repository Name", add a name for your local homework (ex. `path_analysis_soln`)

4. Set privacy level to "Public", then click "Begin Import" button at bottom of the page.

5. Develop your homework solution in the cloned repository and push it to Github when you're done. Extra points for good Git hygiene.

6. Send us the link to your repository.

## Too Easy?

If you thought this was a piece of cake, let's see you do some more cool stuff.

### EStop

We should probably be able to stop the robot from the controller. Modify your program and your `.xml` configuration file to add this capability.

### End Program

Right now, once the KRL program starts, it never ends... Modify your program and your `.xml` file to let the PC terminate RSI controlled motion and send the robot back to home or something.
