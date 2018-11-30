# DRLND Project 1 Report (Navigation)

## Introduction

For this project, I chose to implement the DQN algorithm, based on a [previous implementation](https://github.com/MarcioPorto/deep-reinforcement-learning/tree/master/dqn) for the `LunarLander` Gym environment.
I decided to use DQN because it is a great value-based algorithm that is known to perform well in discrete actions spaces such as the one for this environment. Other algorithms that might work well are SARSA and Q-Learning. I am not including policy-based methods here as they have not been discussed yet in the context of the Deep RL Nanodegree.

## Learning Algorithm

DQN is an algorithm created by DeepMind that brings together the power of the Q-Learning algorithm with the advantages of generalization through function approximation. It uses a deep neural network to estimate a Q-value function. As such, the input to the network is the current state of the environment, and the output is the Q-value for each action.

DeepMind also came up with two techniques that help successfully train a DQN agent:
- *Replay buffer*: Stores a finite collection of previous experiences that can be sampled randomly in the learning step. This helps break the correlation between consecutive actions, which leads to better conversion.
- *Separate target network*: Similar to the local network in structure, this network helps prevent large fluctuations in network updates, which leads to more stable training.

There have been multiple improvements to vanilla DQN suggested by RL researchers. In this project, I decided to implement a method called Double DQN. This method helps prevent the overestimation of Q-values, which is something that DQN agents are susceptible to. It does so by using the main network to pick the best action and the target network to evaluate that action for a given state. The idea here is that the two networks must agree that an action is good.

The DQN implementation for this project also includes soft updates of the target network. This is different from the periodic updates mentioned in the original DeepMind paper. This update mechanism uses the `TAU` hyperparameter. Other important hyperparameters include the `LEARNING_RATE`, `GAMMA` for discounted future rewards, `REPLAY_BUFFER_SIZE`, and the `BATCH_SIZE`, which controls the number of experiences sampled from the replay buffer in the learning step.

The model architecture used is the same for both the local and target networks. It consists of 3 fully-connected layers. The first 2 layers use a ReLU activation, while the output layer has the option of using a softmax activation or no activation.

## Plot of Rewards

For the network architecture, I ended up settling on 96 as the hidden layer's input size and 64 as the hidden layer's output size. As for hyperparameters, I found that my agent performed much better after I increased the size of the replay buffer (`REPLAY_BUFFER_SIZE`) from `1e5` to `2e5`. This makes sense since the agent had more experience tuples to learn from in its update step. Decreasing the `GAMMA` from `0.99` to `0.95` also helped. For the final values of the hyperparameters, please check `dqn_agent.py`.

![Plot of Rewards](https://github.com/MarcioPorto/drlnd-navigation/blob/master/plot_of_rewards.png)

The graph above shows the score for two agents over 1000 episodes. One of the agents used a vanilla DQN implementation, while the other used double DQN in the learn step. Other than this small difference, both agents were trained using the same network structure and hyperparameters. As you can see from above, the two agents perform very similarly in this environment. Across multiple runs, I found that both agents usually solve the environment after about 500-600 episodes, eventually setting at a score close to 16 after 1000 episodes.

I tried comparing the performance of using softmax activation or not in the output layer. I found that while using softmax, the agent never solved the environment. In fact, it did not seem to have learned anything at all after 1000 episodes. Later on, I ended up realizing that using softmax does not make too much sense in this case since nowhere in the implementation I am interested in the probability of picking an action based on the Q-values for each action in a given state. Still, I thought I would note this finding in here as part of my learning experience.

## Ideas for Future Work

To improve upon these results, my main idea is to implement a series of DQN improvements that have been suggested in recent years, including: prioritized experience replay, dueling DQNs, multi-step bootstrap targets, distributional DQN, and noisy DQN. A source of inspiration, and a good reading to get started towards this goal is DeepMind's [Rainbow paper](https://arxiv.org/abs/1710.02298).

Another idea would be to try different agorithms and see how they perform against DQN. Simpler methods such as SARSA and Q-Learning could be used for this purpose, along with many other policy-based methods.