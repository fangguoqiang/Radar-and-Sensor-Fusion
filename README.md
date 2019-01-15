# Radar System design Using Matlab
Rapidly model and simulate phased array systems in the MATLAB and Simulink environments

Provides accurate longitudinal position and velocity measurements over long ranges, but has limited lateral accuracy at long ranges

Generates multiple detections from a single target at close ranges, but merges detections from multiple closely spaced targets into a single detection at long ranges

Sees vehicles and other targets with large radar cross-sections over long ranges, but has limited detection performance for nonmetallic objects such as pedestrians

Responsibilities in a project: 

Create a project to how to set up a radar system simulation consisting of a transmitter, a channel with a target and a receiver.

Skills: MATLAB, DSP System Toolbox


# Create a Tracker
Create a multiObjectTracker to track the vehicles that are close to the ego vehicle. The tracker uses the initSimDemoFilter supporting function to initialize a constant velocity linear Kalman filter that works with position and velocity.

Tracking is done in 2-D. Although the sensors return measurements in 3-D, the motion itself is confined to the horizontal plane, so there is no need to track the height.

tracker = multiObjectTracker('FilterInitializationFcn', @initSimDemoFilter, ...
    'AssignmentThreshold', 30, 'ConfirmationParameters', [4 5]);
positionSelector = [1 0 0 0; 0 0 1 0]; % Position selector
velocitySelector = [0 1 0 0; 0 0 0 1]; % Velocity selector

% Create the display and return a handle to the bird's-eye plot
BEP = createDemoDisplay(egoCar, sensors);
