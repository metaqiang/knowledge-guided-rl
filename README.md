# Accelerating Deep Reinforcement Learning via Knowledge-Guided Policy Network

[![Paper](https://img.shields.io/badge/Paper-Springer-blue)](https://link.springer.com/article/10.1007/s10458-023-09600-1)
[![Journal](https://img.shields.io/badge/Journal-AAMAS-green)](https://www.springer.com/journal/10458)

Official implementation of the paper **"Accelerating Deep Reinforcement Learning via Knowledge-Guided Policy Network"** published in *Autonomous Agents and Multi-Agent Systems* (AAMAS), 2023.

## 📖 Abstract

Deep reinforcement learning has contributed to dramatic advances in many tasks, such as playing games, controlling robots, and navigating complex environments. However, it requires many interactions with the environment. This is different from the human learning process since humans can use prior knowledge, which can significantly speed up the learning process as it avoids unnecessary exploration.

This work proposes a novel framework that combines suboptimal human knowledge with reinforcement learning. Our framework consists of:
- A **fuzzy rule controller** representing human knowledge
- A **refined module** to fine-tune suboptimal prior knowledge

The proposed framework is end-to-end and can be combined with existing reinforcement learning algorithms such as **PPO**, **AC**, and **SAC**.

## 🏗️ Project Structure

```
.
├── main.py                 # Main training script
├── agent.py                # PPO agent implementation
├── controller.py           # Knowledge-guided policy network
├── env.py                  # Gym environment wrapper
├── env_flappybird.py       # FlappyBird environment wrapper
├── logger.py               # Logging utilities
├── utils.py                # Utility functions
├── rule/                   # Fuzzy rule definitions for different environments
│   ├── rule_cartpole.py
│   ├── rule_flappybird.py
│   ├── rule_lunarlander.py
│   ├── rule_lunarlandercontinuous.py
│   ├── rule_mountaincar.py
│   ├── rule_mountaincarcontinuous.py
│   └── rule_pendulum.py
└── ple/                    # PyGame Learning Environment
```

## 🔧 Installation

### Requirements

- Python 3.7
- PyTorch 1.7
- OpenAI Gym 0.16.0
- Weights & Biases (wandb)
- TensorboardX

### Setup

```bash
# Clone the repository
git clone https://github.com/yuyuanq/knowledge-guided-rl.git
cd knowledge-guided-rl

# Install dependencies
pip install torch==1.7.0 gym==0.16.0 wandb tensorboardX pygame
```

## 🚀 Usage

### Training

All logs and model snapshots will be stored in the logging directory. The default logging directory is `./output/ENV_NAME`.

#### Discrete Control Tasks

```bash
# CartPole without Knowledge Controller (baseline)
python main.py --env CartPole-v1 --no_controller --max_update 5000 --seed 0

# CartPole with Knowledge Controller
python main.py --env CartPole-v1 --max_update 5000 --seed 0

# FlappyBird without Knowledge Controller (baseline)
python main.py --env FlappyBird --no_controller --max_update 1200 --seed 0

# FlappyBird with Knowledge Controller
python main.py --env FlappyBird --max_update 1200 --seed 0
```

#### Continuous Control Tasks

```bash
# LunarLander without Knowledge Controller (baseline)
python main.py --env LunarLander-v2 --no_controller --seed 0

# LunarLander with Knowledge Controller
python main.py --env LunarLander-v2 --seed 0

# MountainCarContinuous without Knowledge Controller (baseline)
python main.py --env MountainCarContinuous-v0 --no_controller --continuous --seed 0

# MountainCarContinuous with Knowledge Controller
python main.py --env MountainCarContinuous-v0 --continuous --seed 0

# Pendulum without Knowledge Controller (baseline)
python main.py --env Pendulum-v1 --no_controller --continuous --seed 0

# Pendulum with Knowledge Controller
python main.py --env Pendulum-v1 --continuous --seed 0
```

## 🎮 Supported Environments

| Environment | Type | Knowledge Rules |
|-------------|------|-----------------|
| CartPole-v1 | Discrete | ✅ |
| FlappyBird | Discrete | ✅ |
| LunarLander-v2 | Discrete | ✅ |
| LunarLanderContinuous-v2 | Continuous | ✅ |
| MountainCar-v0 | Discrete | ✅ |
| MountainCarContinuous-v0 | Continuous | ✅ |
| Pendulum-v0/v1 | Continuous | ✅ |

## 📊 Key Components

### Controller (`controller.py`)
The `Controller` class implements the knowledge-guided policy network, which integrates fuzzy logic rules with neural networks.

### Fuzzy Rules (`rule/*.py`)
Each environment has its own rule file containing domain-specific fuzzy rules that encode human prior knowledge about the task.

## 📝 Citation

If you find this work useful in your research, please consider citing:

```bibtex
@article{yu2023accelerating,
  title={Accelerating deep reinforcement learning via knowledge-guided policy network},
  author={Yu, Yuanqiang and Zhang, Peng and Zhao, Kai and Zheng, Yan and Hao, Jianye},
  journal={Autonomous Agents and Multi-Agent Systems},
  volume={37},
  number={1},
  pages={17},
  year={2023},
  publisher={Springer}
}
```
