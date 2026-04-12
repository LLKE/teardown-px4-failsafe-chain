## Experiment

The experiment is performed with QGroundControl and the Gazebo simulator, simulating the PX4 code. The instructions for the entire setup can be found [here](https://docs.px4.io/main/en/simulation/). The selected vehicle is a Quadrotor (x500).

A new failsafe action was introduced: EmergencyClimbHold.

This action is reasoned for the case where we have a data link loss at very low altitudes. To ensure that we are out of danger from near ground obstacles, the drone climbs to a safe altitude and holds there, so that the data link may be recovered. 

This new action is placed after RTL in the severity ranking, as RTL is mission recovery and EmergencyClimbHold is immediate hazard mitigation, which can be treated as more severe when hazard risk dominates.

The drone takes off and we wait for the battery to drain to the critical level, where RTL should normally be triggered. If this can't run for any reason, the failsafe chain resorts to the next more severe failsafe action. 

**Expected**: Drone switches to Land mode and lands where it is.

**Actual**: With a low battery, the drone climbs and holds, leading to the imminent risk of complete battery drain while at a significant altitude.