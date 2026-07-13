# Reinforcement Learning Snake Agent

A collaborative undergraduate research project investigating how reinforcement learning agents learn to play Snake using **Proximal Policy Optimization (PPO)**.

This project was completed as part of the **CRA UR2PhD Undergraduate Research Program** at **UNC Charlotte**.

---

# Overview

The objective of this research was to investigate how a reinforcement learning agent develops strategies over time while playing Snake. Rather than focusing solely on maximizing the final score, the project explored how different reward structures and environment configurations influenced the learning process.

A custom Snake environment was developed using **Gymnasium**, and a **PPO (Proximal Policy Optimization)** agent from **Stable-Baselines3** was trained across multiple experiments. Training performance was evaluated through quantitative metrics and visualizations to better understand the agent's behavior throughout learning.

---

# Research Objectives

- Train a reinforcement learning agent to play Snake.
- Evaluate how reward shaping influences learning.
- Analyze agent performance across multiple training runs.
- Visualize learning progress using experimental data.
- Investigate the strengths and limitations of PPO in a custom environment.

---

# Repository Structure

```text
RL-Snake-Agent/

├── snake_env.py
├── train.py
├── evaluate.py
├── watch.py
├── plot.py
├── test_env.py
├── graphs/
├── paper/
├── results_baseline/
├── results_simple_reward/
├── results_small_grid/
└── README.md
```

---

# Environment

The Snake game was implemented as a custom Gymnasium environment featuring:

- 20 × 20 playing grid
- Relative action space
  - Move Straight
  - Turn Left
  - Turn Right
- 11-dimensional observation space describing:
  - Immediate danger
  - Current movement direction
  - Relative food location
- Reward shaping encouraging efficient movement toward food while penalizing collisions and ineffective movement.

---

# Training

The reinforcement learning agent was trained using:

- Stable-Baselines3
- PPO (Proximal Policy Optimization)
- MLP Policy neural network
- 1,000,000 training timesteps

Training statistics were recorded using Gymnasium's Monitor wrapper and later analyzed using custom plotting scripts.

---

# Evaluation

The repository includes tools for:

- Evaluating trained models
- Visualizing reward curves
- Inspecting trained agent gameplay
- Comparing multiple experimental configurations

---

# Experimental Results

The following plots summarize the learning progress of the PPO agent during training.

## Reward Per Episode During Training

![Reward Curve](Graphs/reward_plot.png)

The reward curve demonstrates a clear upward trend throughout training. Although reinforcement learning naturally exhibits significant variability between episodes, the smoothed moving average shows that the PPO agent consistently improved its policy over time.

---

## Survival Time Per Episode During Training

![Survival Time](Graphs/survival_plot.png)

The survival-time curve shows that the agent survived for progressively longer periods as training continued. This indicates that the learned policy became increasingly effective at avoiding collisions while successfully navigating toward food.

---

## Experimental Summary

| Experiment | Average Score | Average Survival (Steps) | Maximum Score | Primary Observation |
|------------|--------------:|-------------------------:|--------------:|--------------------|
| Baseline (20×20, shaped rewards) | 17.42 | 306.12 | 47 | Established baseline learning performance |
| Simplified reward structure | 19.14 | 353.68 | — | Improved stability and overall performance |
| Smaller grid (10×10) | 14.37 | 151.76 | — | Faster learning within a more constrained environment |

---

## Key Findings

- Simpler reward structures produced more stable learning behavior.
- Reward shaping significantly influenced convergence speed and overall performance.
- Smaller environments accelerated learning but limited long-term performance.
- Reinforcement learning agents should be evaluated using multiple performance metrics rather than relying solely on final score.

---

# Research Paper

The complete research paper documents the project's methodology, experimental design, evaluation process, and findings.

📄 **Read the paper here:** [SnakeRL Research Paper](paper/SnakeRL_Research_Paper.pdf)

The paper discusses:

- Reinforcement learning fundamentals
- PPO training methodology
- Custom Snake environment
- Experimental design
- Performance evaluation
- Results and analysis
- Conclusions

---

# Technologies

- Python
- Gymnasium
- Stable-Baselines3
- NumPy
- Matplotlib
- Pygame

---

# Project Team

This project was completed collaboratively as part of the CRA UR2PhD Undergraduate Research Program.

## Aryan Gadiraju

Primary responsibilities included:

- Designing controlled reinforcement learning experiments
- Modifying reward structures and environment parameters for evaluation
- Training and evaluating PPO agents across multiple experimental configurations
- Collecting and analyzing performance metrics, including reward trends, survival time, and learning stability
- Creating visualizations to interpret agent performance
- Interpreting experimental results and identifying key findings
- Co-authoring the research paper and presentation

## Gracie Vaughn

Primary responsibilities included:

- Designing and implementing the custom Snake environment using Gymnasium
- Developing the reinforcement learning framework and PPO training pipeline
- Implementing the environment logic, observation space, and reward mechanics
- Supporting experimentation and project development throughout the research process

---

# Acknowledgements

This project was completed as part of undergraduate research at **UNC Charlotte** through the **CRA UR2PhD Undergraduate Research Program**.

Special thanks to **Gracie Vaughn** for her collaboration throughout the project and to our faculty mentor for their guidance and support.
