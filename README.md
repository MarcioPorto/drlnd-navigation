[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

# Deep Reinforcement Learning Nanodegree Project 1: Navigation

## Introduction

![Trained Agent][image1]

The files included in this repository implement a DQN agent capable of navigating a large square world with the goal of collecting yellow bananas while avoiding blue bananas.

The environment is similar to that of...

The mechanics of the envonment are as follows:

- *Rewards*: +1 for collecting a yellow banana, -1 for collecting a blue banana.
- *State space*: 37 dimensions (includes agent's velocity, along with ray-based perception of objects around agent's forward direction)
- *Action space*: 4 discrete actions:
    - **`0`** - move forward
    - **`1`** - move backward
    - **`2`** - turn left
    - **`3`** - turn right

The environment is solved once the agent has an average score of +13 over 100 consecutive episodes.

## Setup

1. Clone this repository.

2. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.

3. Place the downloaded file in the folder you cloned this repo to and unzip (or decompress) the file.

## Instructions

1. Open the `Navigation.ipynb` notebook and adjust the path to the environment file based on its name and where you placed it.

2. You are ready to start interacting with the environment. Make sure to run all cells in sections 1 and 2.

- Run cell #X if you want to train the agent again. Feel free to change the hyperparameters in `dqn_agent.py` to see if you can improve training.
- Run cell #X if you want to test the agent. 
    - You can optionally load the model weights from cell #X. Not running that cell will just use the current weights for the `agent` object.