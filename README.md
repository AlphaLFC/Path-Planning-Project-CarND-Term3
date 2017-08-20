# CarND-Path-Planning-Project
My achievement for the Path Planning project of CarND!

## Playground

### Simulator
The Term3 Simulator which contains the Path Planning Project can be downloaded from the [releases tab](https://github.com/udacity/self-driving-car-sim/releases).

### Basic Build Instructions
1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./path_planning`.

### Dependencies
**No need Eigen!**
For more, see details in the [udacity CarND-Path-Planning-Project official repo.](https://github.com/udacity/CarND-Path-Planning-Project)

## Reflections

The car raced smart without incident with longest record of 18 miles (4 laps)!

### Behaviour Planner
I designed three cost to determine how to behave when a slow front car appeared.

- **KL_cost**: defined as $ \sum_i e^{-\Delta s_i}$, where $\Delta s_i$ is the s (in Frenet) between the ego car  and sensed car in the near fulture. Only calculate it when  $\Delta s_i <  0.6 v$. If KL_cost is the least, then the ego car will keep lane and strickly follow the front car.
- **LC_cost**: defined as $ \sum_i e^{-\Delta s_i}$. If the ego car change left and a sensed car is in the safe region, the cost will be calculated. If the ego car is in the most left lane, this cost will be added with 100.
- **RC_cost**: same as LC_cost but for right change.

If KL_cost is more than 0, than the behaviour planner will calculate all costs, and behave by the least cost.

### Trajectory Generator

I follow the walkthrough and finally I got smoothed trajectories.
