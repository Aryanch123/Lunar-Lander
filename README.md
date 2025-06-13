# 🚀 Lunar Lander Agent: Reinforcement Learning with DQN & Actor-Critic

This project implements and compares two reinforcement learning algorithms — **Deep Q-Network (DQN)** and **Actor-Critic** — to train an agent to autonomously land a spacecraft in OpenAI Gym's **LunarLander-v2** environment.

The agent learns optimal control through interaction with the environment, using reward feedback to adjust its policy. The implementation includes training, evaluation, visualization, and performance comparison between both RL methods.

> 🎥 Video demo of trained agent available:  
https://user-images.githubusercontent.com/37583039/219359191-7988e0dc-b1a4-43cc-82d1-4cc18be0d0a2.mp4

---

## 📁 Project Files & Structure

| File/Folder                         | Description                                                                 |
|------------------------------------|-----------------------------------------------------------------------------|
| `agent_class.py`                   | Contains the base agent logic used for both training and evaluation         |
| `train_agent.py`                   | Script to train an agent and save model + training logs                     |
| `run_agent.py`                     | Runs a trained agent and logs performance per episode                       |
| `train and visualize agent.ipynb`  | Jupyter Notebook for training and creating a landing video                  |
| `trained_agents/`                  | Stores saved agent models and performance stats                             |
| `plot_results.ipynb`               | Notebook for analyzing performance after batch training                     |
| `batch_train_and_run.sh`           | Bash script to train 500 agents and evaluate each across 1000 episodes      |

---

## 🎯 Problem Definition

The Lunar Lander environment simulates a spacecraft landing on a lunar surface. The agent must learn to apply engine thrust (left, right, main) to land safely between two flags, minimizing fuel use and avoiding crashes.

- **State Space:** 8 features (position, velocity, angle, leg contact, etc.)
- **Action Space:** Discrete {0: no thrust, 1: left, 2: main, 3: right}
- **Reward Function:** +200 for successful landing, -100 for crashing, -0.3 per frame to penalize fuel usage

---

## 🧠 Algorithms Used

### Deep Q-Network (DQN)
- Experience Replay
- Target Network
- Epsilon-Greedy Strategy
- Double DQN (optional)

### Actor-Critic
- Separate Actor and Critic neural networks
- Policy gradients with value estimation
- Slower convergence, but capable of higher-performing agents in some cases

---

## 📊 Performance Comparison

This project includes a large-scale comparison between the two algorithms:

- **500 agents trained per algorithm**
- **1000 evaluation episodes per trained agent**
- Analyzed:
  - Training speed
  - Number of episodes to converge
  - Distribution of returns
  - Best-performing agent in each group

### 🏁 Sample Results (Customize with Your Plots):

> ![Training Episodes]
> ![training_n_episodes](https://user-images.githubusercontent.com/37583039/227004864-4bc5a4f4-6df3-4edd-a389-af3dbdf8da92.png)
> ![Runtime Comparison]
> ![return_distribution](https://user-images.githubusercontent.com/37583039/227030052-69404955-da7d-4a52-b778-7d3638166308.png)
> ![training_execution_time](https://user-images.githubusercontent.com/37583039/227005536-58dad8cc-1cd4-4c0f-a2c3-53b1f3d6a0fd.png)
> ![Return Distribution]

![return_distribution_best](https://user-images.githubusercontent.com/37583039/227030006-bbb71677-1c2e-4369-8b53-1fc0a7b1f5ac.png)

### Summary of Findings:

- DQN agents **trained faster** and required fewer episodes on average.
- Actor-Critic agents **took longer to train** but occasionally produced **higher peak performance**.
- DQN had **higher mean reward** across agents; however, the **single best agent** came from the Actor-Critic set.

---

## ⚙️ How to Run

### 🐍 Local Setup

```bash
git clone https://github.com/Aryanch123/Lunar-Lander.git
cd Lunar-Lander
pip install -r requirements.txt

