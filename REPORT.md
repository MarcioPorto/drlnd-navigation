# DRLND Project 1 Report (Navigation)

## Introduction

For this project, I chose to implement the DQN algorithm, based on the implementation for the `LunarLander` Gym environment.
I decided to use DQN because it is a great _(action-value function estimating)_ algorithm that is known to perform well in discrete actions spaces such as the one for this environment.

## Algorithm and Implementation

There have been multiple improvements to vanilla DQN suggested by RL researchers. In this project, I decided to change the _(Q next calculation)_ to match that described in the Double DQN algorithm. I did not see a big difference in the performance of the algorithm after this...

Explored the use of softmax activation in the output of the final layer. No real significant difference... Since there was no real, difference I decided not to use softmax in the final layer as to avoid issues floating point issues.

## Results

Looking at the graph below, my best trained agent was able to solve the environment in ___ episodes.

Looking at the agent play, sometimes it gets stuck moving back and forth in an endless loop. 

## Future Work Ideas

Might want to add mechanisms to prevent the agent from being stuck moving back and forth.

I'd also like to look into adding multi-step bootstrap targets, prioritized experience replay and dueling DQNs. With even more time, I'd try to implement the Rainbow agent, as described by [DeepMind]().

## Notes

DQN  +  no softmax      = 627 eps   15.47 average score at 1000 eps
DDQN +  no softmax      = 527 eps   15.28 average score at 1000 eps
DQN  +  softmax         = never     0.02
DDQN +  softmax         = never     -0.08
