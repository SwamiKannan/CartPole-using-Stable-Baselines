# CartPole using Stable Baselines

This is my first exploration of the Stable Baselines library from [Antonin Raffin](https://araffin.github.io/post/sb3/) based on [OpenAI Baseline](https://github.com/Stable-Baselines-Team/stable-baselines/blob/master/docs/index.rst)

## Renders
### Random
<p align="center">
<img src="https://github.com/SwamiKannan/CartPole/blob/main/PPO/render/base_performance/random.gif"
</p>

### Modelled
<p align="center">
<img src="https://github.com/SwamiKannan/CartPole/blob/main/PPO/render/model_performance/modelled.gif"
</p>

## CartPole Introduction

## Setup
Cartpole - known also as an Inverted Pendulum is a pendulum with a center of gravity above its pivot point. It’s unstable, but can be controlled by moving the pivot point under the center of mass. The goal is to keep the cartpole balanced by applying appropriate forces to a pivot point.
<p align="center">
<img src="https://github.com/SwamiKannan/CartPole/blob/main/cartpole_schema.png"
</p>
<p align ="center">
<b><i>    Violet square indicates a pivot point<br>
    Red and green arrows show possible horizontal forces that can be applied to a pivot point<br>
</b></i> 
    </p>
    <i>A pole is attached by an un-actuated joint to a cart, which moves along a frictionless track. The system is controlled by applying a force of +1 or -1 to the cart. The pendulum starts upright, and the goal is to prevent it from falling over. A reward of +1 is provided for every timestep that the pole remains upright. The episode ends when the pole is more than 15 degrees from vertical, or the cart moves more than 2.4 units from the center.</i>

Take a look at a video below with a real-life demonstration of a cartpole problem learning process.
<p align ="center">
[![CartPole in real life](https://img.youtube.com/vi/XiigTGKZfks/0.jpg)](https://www.youtube.com/watch?v=XiigTGKZfks&t=130s)
</p>

### Source code for environment:
https://github.com/openai/gym/blob/master/gym/envs/classic_control/cartpole.py

### States Space:
The observation is a `ndarray` with shape `(4,)` where the elements correspond to the following:

| Num | Observation           | Min                  | Max                |
|-----|-----------------------|----------------------|--------------------|
| 0   | Cart Position         | -4.8*                | 4.8*               |
| 1   | Cart Velocity         | -Inf                 | Inf                |
| 2   | Pole Angle            | ~ -0.418 rad (-24°)**| ~ 0.418 rad (24°)**|
| 3   | Pole Angular Velocity | -Inf                 | Inf                |




Note:
The table denotes the ranges of possible observations for each element, but in two cases this range exceeds the range of possible values in an un-terminated episode: <br>*: the cart x-position can be observed between (-4.8, 4.8), but an episode terminates if the cart leaves the (-2.4, 2.4) range. <br>** : Similarly, the pole angle can be observed between (-.418, .418) radians or precisely ±24°, but an episode is terminated if the pole angle is outside the (-.2095, .2095) range or precisely ±12° Starting State All observations are assigned a uniform random value between (-0.05, 0.05) Episode Termination The episode terminates of one of the following occurs:
1. Pole Angle is more than ±12°
2. Cart Position is more than ±2.4 (center of the cart reaches the edge of the display)
3. Episode length is greater than 500 (200 for v0)
Rewards:
Reward is 1 for every step taken, including the termination step. The threshold is 475 for v1.
Action Space:
The agent  takes a 1-element vector for actions. The action space is (action) in [0, 1], where `action` is used to push the cart with a fixed amount of force:
Num Action 0 Push cart to the left
1 Push cart to the right

Note: The amount the velocity is reduced or increased is not fixed as it depends on the angle the pole is pointing. This is because the centre of gravity of the pole increases the amount of energy needed to move the cart underneath it

## Stable Baselines:
Stable Baselines3 is a set of reliable implementations of reinforcement learning algorithms in PyTorch. It is the next major version of Stable Baselines. These algorithms will make it easier for the research community and industry to replicate, refine, and identify new ideas, and will create good baselines to build projects on top of.
https://stable-baselines3.readthedocs.io/en/master/index.html)

Stable Baselines contrib
https://sb3-contrib.readthedocs.io/en/master/index.html

## Algorithms:
1. [PPO](https://stable-baselines3.readthedocs.io/en/master/modules/ppo.html)

## Environments:
1. [Cartpole-v0](https://www.gymlibrary.ml/environments/classic_control/cart_pole/)  
