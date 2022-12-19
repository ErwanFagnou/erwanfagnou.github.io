---
title: "[Contest] Swarm Rescue Challenge"
excerpt: "A 6-month contest about controlling drones to rescue people in a collapsed building."
collection: projects
teaser: "/images/projects/challenge_swarm_rescue/debug.mp4"
teaser_type: "video"
teaser_video_hover: false
---

<div style="text-align: right"> <a href="https://github.com/embaba/swarm-rescue" target="_blank"><i class="fab fa-fw fa-github" aria-hidden="true" style="color: #000"></i>Github of the contest</a> </div>

<ins>Ranking:</ins> **1st place** (€8000)

<ins>Teammate:</ins> Nicolas Micaux

## The contest
The DGA (Direction Générale de l'Armement) organized a 6-month contest for students to design an algorithm to control a swarm of drones in a simulation. The goal was to rescue people in an unknown building, as fast as possible. The drones were equipped with multiple sensors (GPS, Lidar, touch sensors, velocity sensor...) that had some noise, and that could fail to work in some special areas of the building. They were also able to communicate with each other within a certain range.

## Our solution
As the contest is being held again this year, please understand that we cannot disclose too many details about our solution, and our code cannot be public. However, we can give some general ideas about our approach:
- **Sensors**: We relied on various statistical / signal processing methods to denoise the different sensors and extract relevant information.
- **Cartography**: As the building map was unknown, the drones used the lidar data to build a map (as a 2D grid). Because the resulting map was a bit noisy and not usable as is, we used a deep learning model to denoise it.
- **Communication**: The drones communicated their knowledge to the drones in their vicinity, with a lot of mind-bending algorithms to merge the information received, and to reduce the amount of data sent.
- **Planning**: Once the map was built, we used corner detection to create a more abstract graph of the map (the black lines in the video below). We then used an MCTS algorithm to explore the possible decisions and choose the best one for each drone. The drones were trying to maximize a heuristic function, which was taking into account the number of people saved, the time spent, the area explored, etc.

{% include project_video.html
path="/images/projects/challenge_swarm_rescue/swarm_rescue_full.mp4"
caption="Sample video of our drones (in blue) rescuing people (in orange) by bringing them back to the rescue zone (in red). The colored rectangles are special zones: red deactivates communication, blue deactivates the GPS, and gray kills the drones that enter it."
%}

{% include project_video.html
path="/images/projects/challenge_swarm_rescue/debug.mp4"
caption="Everything one drone (in black) sees. What is displayed is computed from its observations and the messages received from the other drones. Its planned path is shown with solid white lines, and the lines are dashed for the other drones. Black lines represent the graph used to compute the trajectory in the building. Note that drones cannot communicate if they are far from each other, so information can take some time before being updated."
%}