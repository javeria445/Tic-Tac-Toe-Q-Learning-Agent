# Tic-Tac-Toe Q-Learning Agent

A Python implementation of Tic-Tac-Toe featuring a Reinforcement Learning agent trained using the **Q-Learning algorithm**.

The AI agent learns to play as **X** through repeated gameplay and uses an epsilon-greedy strategy to balance exploration and exploitation.

## Features

- Human vs Human gameplay
- Human vs AI gameplay
- Q-Learning based AI agent
- 500,000 training episodes
- Epsilon-greedy exploration
- Reward shaping
- Eligibility trace for penalizing losing game histories
- Smart opponent with priority-based decision making
- Random opponent for benchmarking
- Q-table persistence using Python `pickle`
- Benchmarking over 5,000 evaluation games
- AI opens from the center as required by the lab specification

## Q-Learning Configuration

The agent uses the following parameters:

- Learning rate (α): `0.3`
- Discount factor (γ): `0.95`
- Initial epsilon: `1.0`
- Minimum epsilon: `0.01`
- Epsilon decay: `0.999985`
- Training episodes: `500,000`

## State Representation

Each Tic-Tac-Toe board is represented as a 9-character string.

Example:

```text
123X56O89
```

The board is read from left to right and top to bottom.

No symmetry transformation is applied so that different board positions remain separate states in the Q-table.

## Reward Shaping

The agent receives intermediate rewards to improve learning:

| Event | Reward |
|---|---:|
| AI wins | +10 |
| Blocks opponent's winning move | +3 |
| Creates a fork | +2 |
| Game ends in draw | +0.5 |
| AI loses | -10 |

When the AI loses, the loss penalty is propagated backward through all moves made during the game using a discounted eligibility trace.

## Opponent Strategy

The smart opponent follows this priority:

1. Win
2. Block
3. Create Fork
4. Block Fork
5. Center
6. Corner
7. Edge

Training consists of:

- 85% games against the smart opponent
- 15% games against a random opponent

## Training

The agent is trained for **500,000 episodes**.

During training, epsilon gradually decreases so that the agent initially explores random actions and eventually relies more heavily on learned Q-values.

The learned Q-table is saved using Python's `pickle` module.

```text
q_table_fixed.pkl
```

## Benchmark Results

After 500,000 training episodes, the agent was evaluated over 5,000 games.

### Against Random Opponent

- Win: **96.5%**
- Draw: **3.5%**
- Loss: **0.0%**

### Against Smart Opponent

- Win: **0.0%**
- Draw: **100.0%**
- Loss: **0.0%**

The results show that the trained agent effectively avoids losing against the smart opponent while achieving a very high win rate against a random opponent.

## How to Run

Make sure Python 3 is installed.

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/tic-tac-toe-q-learning.git
```

Move into the project directory:

```bash
cd tic-tac-toe-q-learning
```

Run the Python program:

```bash
python tic_tac_toe.py
```

> Replace `tic_tac_toe.py` with the actual Python filename if your file has a different name.

## Project Structure

```text
tic-tac-toe-q-learning/
│
├── tic_tac_toe.py
├── q_table_fixed.pkl
├── README.md
```

The exact files may vary depending on the final project implementation.

## Technologies

- Python
- Reinforcement Learning
- Q-Learning
- Python Dictionary
- Pickle
- Random/Epsilon-Greedy Exploration

## Learning Objectives

This project demonstrates:

- Reinforcement Learning fundamentals
- Q-Learning
- State-action value estimation
- Epsilon-greedy exploration
- Reward shaping
- Eligibility traces
- Self-interaction with an environment
- AI benchmarking and evaluation
- Persistence of learned models

## Limitations

- The agent is designed specifically for 3×3 Tic-Tac-Toe.
- The Q-table approach does not scale efficiently to larger state spaces.
- The epsilon decay schedule is fixed.
- The opening move is hardcoded to the center.
- The learned Q-table is stored entirely in memory.
- The agent does not generalize directly to different board sizes.

## Future Improvements

Possible improvements include:

- Implementing a Deep Q-Network (DQN)
- Training through true self-play
- Comparing Q-Learning with Monte Carlo Tree Search (MCTS)
- Extending the game to larger board sizes
- Adding a web-based graphical interface
- Implementing prioritized experience replay
- Experimenting with adaptive epsilon decay

## Author

**Javeria Anis**

BS Cyber Security  
COMSATS University Islamabad
