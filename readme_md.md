# Autonomous Snake Game (Reinforcement Learning)

![Python Version](https://img.shields.io/badge/Python-3.13-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-orange.svg)
![Pygame](https://img.shields.io/badge/Pygame-Game%20Engine-green.svg)
![Reinforcement Learning](https://img.shields.io/badge/RL-Deep%20Q--Learning-red.svg)

An autonomous agent that learns to play the classic Snake game from scratch using **Deep Q-Learning (DQN)** and **PyTorch**. The AI agent receives no pre-programmed rules or hardcoded paths; instead, it relies entirely on a reward system, trial-and-error experience replay, and neural network optimization to master optimal gameplay.

---

## 📌 Project Overview

This project demonstrates the practical application of **Reinforcement Learning (RL)** to an environment built with **Pygame**. 

* **Goal:** Train an AI agent to maximize its high score by eating food while avoiding collisions with walls and its own body.
* **Core Technique:** Deep Q-Network (DQN) with Bellman Equation optimization and Experience Replay.
* **Architecture:** Modular, separation-of-concerns structure (`game.py`, `model.py`, `agent.py`, `helper.py`).

---

## 🚀 Key Features

* **Self-Learning AI:** Starts with zero knowledge (random exploration) and transitions to strategic decisions (exploitation) as training progresses.
* **Modular Clean Code:** Decoupled game logic, neural network model, and agent training modules.
* **Real-time Performance Plotting:** Live graph visualizing score evolution and running average score using `matplotlib`.
* **Automatic Checkpointing:** Automatically saves the best model state (`model.pth`) whenever a new high score is achieved.

---

## 🛠️ Tech Stack & Dependencies

* **Python 3.13** — Core language
* **PyTorch** — Neural network construction, backpropagation, and loss evaluation
* **Pygame** — Game canvas rendering, frame processing, and event mechanics
* **NumPy** — Vector and matrix manipulation for state representations
* **Matplotlib** — Real-time progress plotting and visualization

---

## 📂 Directory Structure

```text
SnakeAI/
│
├── game.py       # Pygame engine handling game loop, renders, and collisions
├── model.py      # PyTorch Linear_QNet architecture and QTrainer logic
├── agent.py      # Agent environment state extraction, memory replay, and loop
├── helper.py     # Live performance plotting utility using Matplotlib
└── model/        # Output directory for saved model weights (model.pth)
```

---

## 🧠 Algorithmic Architecture & Deep Q-Learning Mechanics

### 1. State Representation (11 Inputs)
The agent perceives the current environment state via an **11-dimensional boolean vector**:

| Index | Feature | Description |
| :--- | :--- | :--- |
| `0 - 2` | **Danger Detection** | Danger Straight, Danger Right, Danger Left |
| `3 - 6` | **Current Direction** | Moving Left, Moving Right, Moving Up, Moving Down |
| `7 - 10` | **Food Location** | Food Left, Food Right, Food Up, Food Down |

### 2. Action Space (3 Outputs)
Actions are represented as 3-element one-hot encoded vectors relative to the snake's current heading:
* `[1, 0, 0]` $\rightarrow$ **Straight**
* `[0, 1, 0]` $\rightarrow$ **Turn Right**
* `[0, 0, 1]` $\rightarrow$ **Turn Left**

### 3. Reward System
* **Eat Food:** $+10$
* **Collision / Game Over:** $-10$
* **Standard Step:** $0$

### 4. Neural Network Architecture (`Linear_QNet`)
* **Input Layer:** 11 nodes (State vector)
* **Hidden Layer:** 256 nodes (ReLU activation)
* **Output Layer:** 3 nodes (Q-values for each action)
* **Optimizer:** Adam ($\text{lr} = 0.001$)
* **Loss Function:** Mean Squared Error (MSE Loss) via Bellman Equation:
  $$Q(s, a) = r + \gamma \cdot \max Q(s', a')$$

---

## ⚙️ Installation & Usage

### 1. Clone or Create the Directory
```powershell
git clone https://github.com/your-username/SnakeAI.git
cd SnakeAI
```

### 2. Install Dependencies
Using Python 3.13 explicitly:
```powershell
& "C:\Users\Javoh\AppData\Local\Programs\Python\Python313\python.exe" -m pip install pygame torch numpy matplotlib
```
*(Or standard standard pip command: `pip install pygame torch numpy matplotlib`)*

### 3. Run the Training Agent
```powershell
& "C:\Users\Javoh\AppData\Local\Programs\Python\Python313\python.exe" agent.py
```

---

## 📈 Learning Process

1. **Games 0 – 30 (Exploration):** The agent moves largely at random ($\epsilon$-greedy policy) to explore the state space. Expect frequent wall and body collisions.
2. **Games 30 – 80 (Transition):** Short-term and long-term memory updates allow the agent to associate moving towards food with positive rewards and wall collisions with penalties.
3. **Games 80+ (Exploitation):** The agent relies on its trained PyTorch model to actively navigate around its own body, collect food, and continuously hit high scores.

---

## 👤 Author

* **Abduraxmonov Javoxir** — *IT PM & AI Specialist / Junior AI Engineer*
* **Email:** javohirjavoh8206@gmail.com
* **Telegram:** [@javoxir_abduraxmonov](https://t.me/javoxir_abduraxmonov)