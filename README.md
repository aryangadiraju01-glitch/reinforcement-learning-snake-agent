# SnakeRL

A reinforcement learning agent trained to play Snake, built from scratch as part of an undergraduate research project on how agents learn.

## Overview

This project explores how a reinforcement learning agent develops strategy over time. Rather than optimizing purely for high scores, the goal was to understand the learning process itself: how an agent's behavior evolves as it trains, and how changes to its environment affect that evolution.

To do this, I built the Snake game as a custom [Gymnasium](https://gymnasium.farama.org/) environment from scratch, then trained a Proximal Policy Optimization (PPO) agent on it using Stable-Baselines3. Training data was logged and visualized across multiple runs to study the agent's learning curve.

## How It Works

**Environment (snake_env.py)**
- 20x20 grid, implemented as a custom Gymnasium environment
- **Action space:** 3 discrete actions — go straight, turn right, turn left (relative to the snake's current direction)
- **Observation space:** an 11-value vector describing the snake's immediate surroundings — danger detection (straight/left/right), current movement direction, and the food's relative position
- **Reward shaping:** +10 for eating food, -10 for dying (wall or self-collision), and a small +1/-1 shaping reward based on whether the snake moved closer to or farther from the food

**Training (train.py)**
- Trains a PPO agent (Stable-Baselines3, `MlpPolicy`) for 1,000,000 timesteps
- Wraps the environment in a `Monitor` to log episode rewards and lengths during training

**Evaluation & Visualization (evaluate.py, plot.py, watch.py)**
- `evaluate.py` runs the trained model and measures performance
- `plot.py` graphs training data (reward/score over time) from the training logs
- `watch.py` renders a trained agent playing in real time using Pygame, so you can visually inspect its behavior

**Manual testing (test_env.py)**
- Lets you step through the environment manually to verify game logic before training

## Tech Stack

Python, [Gymnasium](https://gymnasium.farama.org/), [Stable-Baselines3](https://stable-baselines3.readthedocs.io/) (PPO), NumPy, Pygame (rendering), Matplotlib (training plots)

## Running It

**Install dependencies**
- pip install gymnasium stable-baselines3 pygame numpy matplotlib

**Train the agent (1,000,000 timesteps)**
- python train.py

**Watch the trained agent play**
- python watch.py

**Evaluate performance**
- python evaluate.py

**Plot training progress**
- python plot.py
