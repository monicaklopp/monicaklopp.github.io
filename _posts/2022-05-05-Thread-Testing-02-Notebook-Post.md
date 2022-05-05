---
layout: post
title: Thu. Apr. 28, 2022
subtitle: Second Notebook Post - Thread Testing
gh-repo: monicaklopp/monicaklopp.github.io
gh-badge: [star, fork, follow]
tags:
comments: true
---

Today we will do a first round of thread tests on the controls.
Animals tested were T01 and T02.
Data will be input in [this](https://docs.google.com/spreadsheets/d/1GxLnNJjjjZ8xhBzz8nD-eUdpOwg6UY7yicG7ER5YIOQ/edit?usp=sharing) google sheet.

The general procedure will be as follows:

## Setup procedure
1. Open labview Program Omega DFG51-2 Force Gauge Logger.vi
2. Open Amscope
3. Open the google sheet
4. Turn on the lights



## Run Test
1. Wet and clean the sample with seawater.
2. Take a picture of the thread plaque using Amscope software.
3. Calibrate the image and record the cross-sectional area in the google sheet and record the conversion factor.
4. Turn on the force gauge by hitting the power button.
5. Cut the sheet as needed and grip the thread using the hemostat clamp.
6. Hang the clamp off of the force gauge.
7. Push the down button on the motor and let it run until the sheet is laying flat and there is slack in the thread.
8. Using the forceps, hold the sheet down and hit zero button.
9. Start the labview logger software by hitting the arrow run button.
10. Flip the motor switch up and record the data.
11. Monitor the thread plaque during failure and record failure mode (see figure 1 below).
12. After failure, hit the stop button and save the file with .txt extension.
13. After one animal is finished, return to stack and write that it was tested.

## End of Day Shutdown Procedure
1. Turn off the force gauge.
2. Clean workspace.
3. Bind up the rest of the samples.
4. Turn off the lights.
5. Go to GitHub desktop and add summary, commit to main, and push it.

![](/post_images/20220428/failure_mode.png)
Figure 1. Failure modes. c) Tearing, d) Peeling, e) Cohesive.
