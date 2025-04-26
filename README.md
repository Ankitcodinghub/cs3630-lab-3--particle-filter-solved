# cs3630-lab-3--particle-filter-solved
**TO GET THIS SOLUTION VISIT:** [CS3630 LAB 3- PARTICLE FILTER Solved](https://www.ankitcodinghub.com/product/cs-3630-introduction-to-robotics-and-perception-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;126743&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;3&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (3 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS3630 LAB 3- PARTICLE FILTER Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (3 votes)    </div>
    </div>
&nbsp;

The objective of Lab 3 is to implement a particle filter (a.k.a. Monte Carlo Localization). In this lab, you will work entirely in simulation to validate your algorithm.

Recall that a particle filter repeats these main steps:

• A motion update step, in which the particles representing the robot’s potential location are updated according to the motion control command sent to the robot

• A measurement update step, in which each particle is weighted according to the likelihood of its position being correct given the sensor inputs

In this lab, we provide skeleton code in utils.py and particle_filter.py, and your job is to fill in the missing pieces. Please start by implementing the three missing functions in utils.py. We provide unit tests for these functions in local_tests.py.

IMPORTANT: the autograder for this lab is slow (will take around 5 minutes to finish grading) and not helpful for debugging purposes (we hide the test cases). To debug your implementation, we strongly recommend using the local unit tests and local simulator instead of the autograder. This will allow you to get feedback more quickly and see how the particle filter is actually behaving.

To run the local tests for utils.py, call python3 local_tests.py in your terminal.

To run the local simulator, call python3 pf_gui.py in your terminal. (Note this will not work until you implement a sufficient number of the missing functions.)

Below, we provide more information on the local simulator, some helpful tips for implementing a particle filter, and additional details on grading and submission.

Figure 1: A correctly implemented particle filter. Notice (nearly) all the particles have converged around the same estimate.

Simulator: After launching the local simulator, you will see a GUI window that shows the world/robot/particles. The ground truth robot pose will be shown as red (with dashed line to show FOV). Particles will be shown as red dot with a short line segment indicate the heading angle, and the estimated robot pose (average over all particles) will be shown in grey (if not all particles meet in a single cluster) or in green (all particles meet in a single cluster, meaning your estimation has converged).

Two types of simulated robot motion are implemented in pf_gui.py: (1) The robot drives forward until it hits an obstacle, then it bounces in a random direction and repeats. (2) The robot drives in a circle (this is the motion the autograder uses). Feel free to change the setup at the top of pf_gui.py for debugging.

Coordinate frames: One of the key challenges in implementing a particle filter (or mobile robotics in general) is coordinating coordinate frames. We provide a diagram to help you with this in Figure 2. The world has the origin (0,0) at the bottom left, X axis points right and Y axis points up. The robot has a local frame in which the X axis points to the front of the robot, and Y axis points to the left of the robot. You will have to handle the difference between local robot frame and global gridworld frame in the motion update.

Figure 2: Coordinate frame definitions

Motion update details: the input of the motion update function includes particles representing the belief 𝑝(𝑥𝑡−|𝑢𝑡−1) before motion update, and the robot’s new odometry measurement. The odometry measurement is the relative transformation of current robot pose relative to last robot pose, in last robot’s local frame, as shown in Fig 2. To simulate noise in a real-world environment, the odometry measurement given to you includes Gaussian noise. The output of the motion update function should be a set of particles representing the belief 𝑝(𝑥𝑡|𝑥𝑡−1, 𝑢𝑡) after motion update. Your motion update must account for the noise in the odometry measurement in order for your filter to converge properly.

Figure 2: Odometry measurement transform

Measurement update details: the input of the measurement update function includes particles representing the belief 𝑝(𝑥𝑡|𝑥𝑡−1, 𝑢𝑡) after motion update, and the list of localization marker observation measurements. The marker measurement is calculated as a relative transformation from robot to the marker, in the robot’s local frame, as shown in Fig 3. Same as odometry measurement, marker measurements are also given to you with Gaussian noise. The output of your measurement update function should be a set of particles representing the belief after the measurement update and resampling.

Figure 3: Marker measurement transform

two matching as:

𝑑𝑖𝑠𝑡𝐵𝑒𝑡𝑤𝑒𝑒𝑛𝑀𝑎𝑟𝑘𝑒𝑟𝑠2 𝑎𝑛𝑔𝑙𝑒𝐵𝑒𝑡𝑤𝑒𝑒𝑛𝑀𝑎𝑟𝑘𝑒𝑟𝑠2

−( 2 + 2 )

𝑃(𝑥) = 𝑒 2𝜎𝑡𝑟𝑎𝑛𝑠 2𝜎ℎ𝑒𝑎𝑑

The relevant standard deviations can be found in settings.py.

Grading: Your grade on Gradescope is your final grade. The autograder evaluates whether:

1. [50 points] Your filter’s estimation can converge to correct value within a reasonable number of iterations.

2. [50 points] Your filter can accurately track the robot’s motion.

More details on grading: We use a total of 5000 particles, and we treat the average of all 5000 particles as the filter’s estimation. The particles will be initialized randomly in the space. We define the estimation as correct if the translational error between ground truth and filter’s estimation is smaller than 1.0 unit (grid unit), and the rotational error between ground truth and filter’s estimation is smaller than 10 degrees. The grading is split into two stages, the total score is the sum of two stages:

1. We let the robot run 95-time steps to let the filter find global optimal estimation. If the filter gives correct estimation in 50 steps, you get the full credit of 50 points. If you take more than 50 steps to get the correct estimation, a point is deducted for each additional step required. Thus, an implementation that takes 66 steps to converge will earn 34 points; one that does not converge within 95 steps will earn 0 points. For reference, our implementation converges within approximately 10 steps.

2. We let the robot run another 100-time steps to test stability of the filter. The score will be calculated as 50*p, where p is the percentage of “correct” pose estimations based on the position and angle variance listed above.

3. Note: we round all scores to the nearest integer (up or down as needed).
