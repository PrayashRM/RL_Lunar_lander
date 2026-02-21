---
library_name: stable-baselines3
tags:
- LunarLander-v2
- deep-reinforcement-learning
- reinforcement-learning
- stable-baselines3
model-index:
- name: PPO
  results:
  - task:
      type: reinforcement-learning
      name: reinforcement-learning
    dataset:
      name: LunarLander-v2
      type: LunarLander-v2
    metrics:
    - type: mean_reward
      value: 276.50 +/- 26.10
      name: mean_reward
      verified: false
widget:
- id: "YOUR_HF_USERNAME/ppo-LunarLander-v2"
  src: "replay.mp4"
  type: video
---

# 🚀 PPO Agent Playing LunarLander-v2

This is a trained model of a **PPO (Proximal Policy Optimization)** agent playing **LunarLander-v2** using the [Stable-Baselines3](https://github.com/DLR-RM/stable-baselines3) library.

The agent has been trained to land safely between the yellow flags, optimizing for fuel efficiency and landing stability.

### 🎥 Agent Performance
<div align="center">
  <h3>🤖 Watch the Agent Land!</h3>
  <video controls autoplay loop muted src="https://huggingface.co/Subcon/ppo-LunarLander-v2/resolve/main/replay.mp4" width="100%"></video>
</div>

### 🏆 Metrics
- **Mean Reward:** `276.50 +/- 26.10`
- **Environment:** `LunarLander-v2`
- **Algorithm:** `PPO`

### 💻 Usage (Run this model)

You can download and run this model using the following code:

```python
import gymnasium as gym
from stable_baselines3 import PPO
from stable_baselines3.common.vec_env import DummyVecEnv, VecNormalize

# 1. Create the environment
env = DummyVecEnv([lambda: gym.make("LunarLander-v2", render_mode="human")])

# 2. Load the trained model (from Hugging Face)
# Note: You need to replace "YOUR_HF_USERNAME" with your actual username
model = PPO.load_from_hub(
    repo_id="YOUR_HF_USERNAME/ppo-LunarLander-v2",
    filename="ppo-LunarLander-v2.zip",
)

# 3. Enjoy the trained agent
obs = env.reset()
done = False
while not done:
    action, _ = model.predict(obs)
    obs, _states, done, info = env.step(action)
    env.render()


