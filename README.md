# dino.game
Explanation of the Game
The Dino Game is a classic arcade-style game where the goal is to control a dinosaur that jumps over incoming obstacles. This game is similar to the Google Dino Game that appears in Chrome when you’re offline. The game is built using Pygame for rendering and Gymnasium for environment management, which allows for easy integration with reinforcement learning agents.

Dino (Character)
The Dino is represented by a simple black rectangle.
The Dino can jump (represented by increasing and decreasing its y position).
The Dino starts at the ground level (GROUND_HEIGHT - DINO_HEIGHT), and it must avoid obstacles that come toward it.
Obstacle
The obstacle is represented by a red rectangle that moves from the right to the left of the screen.
Once the obstacle passes the left side of the screen, it resets to the right, and the score increments.
Game Mechanics
The game ends if the Dino collides with the obstacle.
The jumping mechanism allows the Dino to rise and fall based on gravity, which is handled by updating the Dino's y position.
State
The state of the game is represented by a vector with 4 values:

Dino’s y-position (self.dino_y): The vertical position of the Dino on the screen.
Obstacle’s x-position (self.obstacle_x): The horizontal position of the obstacle on the screen. It decreases over time, simulating movement from right to left.
Obstacle speed (self.obstacle_speed): The speed at which the obstacle moves leftward. It is kept constant for simplicity, but can be increased to make the game harder.
Score (self.reward): The current score of the game. The score increments when an obstacle moves past the left side of the screen, and it decreases by 5 if the Dino collides with the obstacle.
Action
The game uses discrete actions, meaning there are two possible actions that can be performed:

Action 0: Do nothing. The Dino remains on the ground.
Action 1: Jump. The Dino performs a jump, if not already jumping.
The jump action is triggered by pressing the spacebar. When the action is triggered, the Dino’s vertical position is updated based on gravity (simulated by the dino_velocity).

Reward
The reward is defined as follows:

+1 reward for each obstacle successfully avoided (when the obstacle moves off-screen).
-5 penalty if the Dino collides with the obstacle.
This reward system encourages the agent to learn to avoid obstacles and penalizes it for collisions, motivating the agent to avoid risky behavior.

Instructions to Run the Game
Make a copy of this repository:
Clone or download the repository where the code is stored.

To clone the repository using Git:
bash
Copy
git clone https://github.com/your-username/dino-game.git
Run game.py:
After cloning the repository, navigate to the directory where the files are stored, and run the game.py script to play the Dino game.

Run the following command in the terminal:
bash
Copy
python game.py
The game will open in a Pygame window. You control the Dino by pressing the spacebar to make it jump. The game tracks your score and ends when the Dino collides with an obstacle.
Instructions to Train RL (DQN) Agent
To train a reinforcement learning agent using DQN (Deep Q-Network), follow these steps:

Make a copy of this repository:
Clone or download the repository where the code is stored.

To clone using Git:
bash
Copy
git clone https://github.com/your-username/dino-game.git
Run train_agent.py:
After cloning the repository, navigate to the directory and run the train_agent.py script to start training the agent.

Run the following command:
bash
Copy
python train_agent.py
The script will train a DQN agent on the Dino game environment (DinoGame-v0). The agent will learn to play the game by interacting with the environment and optimizing its actions based on the rewards it receives. The model will be saved after training and can be used for testing or further evaluation.

Key Components for Training the Agent:
Stable Baselines3 (DQN):

The DQN (Deep Q-Network) algorithm is used for training the agent. It helps the agent learn how to map states to actions to maximize long-term rewards.
The model.learn(total_timesteps=800000) method is used to train the agent for 800,000 timesteps, which could be adjusted to experiment with different training durations.
Callback for Reward Logging:

A RewardLoggerCallback is used to track the rewards during training and log the agent's learning progress.
Gymnasium:

The game environment is created using Gymnasium, which is a library that standardizes reinforcement learning environments and simplifies agent training.
Contributions
Created at TUMO:
This project was developed as part of a TUMO initiative. TUMO provides a great environment for learning programming, game development, and AI.

Used Gymnasium:
The Gymnasium library was used to create the environment for the Dino game, allowing it to be easily integrated with RL algorithms. It provides a standardized interface for defining environments and interacting with them using reinforcement learning agents.

Used Stable Baselines3:
The Stable Baselines3 library, which includes pre-built reinforcement learning algorithms, was used to train the DQN agent. Stable Baselines3 simplifies the process of setting up and training RL agents on custom environments like the Dino Game.

Extra Features
GIF Animation on Start Screen:
The game includes a feature to display an animated GIF during the start screen. The play_gif() function is used to load and play a GIF on the screen using the Pillow library, creating a smooth animation experience.

Interactive Start Screen:
The game includes a starting screen with two options: Start Game and Watch Video. The player can choose to start the game or view an animation (GIF) before proceeding to the actual game. This is handled using Pygame’s event handling system.

This Dino game project integrates simple mechanics with reinforcement learning and allows you to test and train agents using deep learning techniques. It’s a fun, interactive example of applying RL to a traditional arcade-style game!



