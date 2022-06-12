The path planning procedure consists of 4 steps. 

1. Filter out the vehicles that can impact the decision-making (e.g., leading vehicle and close enough vehicles on adjacent lanes) from all vehicles in the localization data.
2. Use the markov state machine to determine what is the next decision: change to left/right lane or accelerate/decelerate in current lane.
3. Generate a smooth trajectory by fitting a spline using several anchor points and output the path using the fitted spline.

I noticed that when determining whether the left/right lane was available for lane changing, if we use a fixed distance threshold (e.g., 30m used in the Q\&A video), collisions might happen during the lane changing process when there were high-speed vehicle coming from behind. So I change it to a value that is  relavent to the speeds of ego vehicle and the vehicle coming from behind.