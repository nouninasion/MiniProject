# NPC Maze Solver with Reinforcement Learning

This project demonstrates how a Non-Player Character (NPC) can learn to find the shortest path through a randomly generated maze using the Q-learning reinforcement learning algorithm. The maze and the learning process are visualized in a web browser using HTML, CSS, and JavaScript.

## How to Run the Project

1.  **Save the Files:** Ensure you have saved the provided code into three separate files in the same directory:
    * `index.html` (for the HTML structure)
    * `style.css` (for the CSS styling)
    * `script.js` (for the JavaScript logic)

2.  **Open in Browser:** Simply open the `index.html` file in any modern web browser (Chrome, Firefox, Safari, etc.).

3.  **Start Learning:** Once the page is loaded, you will see a randomly generated 10x10 maze with a 'S' (Start) and 'F' (Finish) marker. Click the "Start Learning" button below the maze.

4.  **Observe the Learning Process:**
    * The NPC (represented by a yellow circle) will start exploring the maze.
    * The "Episode" counter will increment from 0 to 100, indicating the number of training iterations.
    * "Total Reward (Episode)" shows the reward obtained by the NPC in the current episode.
    * "Langkah (Episode)" displays the number of steps taken by the NPC in the current episode.
    * "Epsilon" shows the current exploration-exploitation rate. It will decrease over time, encouraging the NPC to exploit its learned knowledge.
    * "Rata-rata Reward (50 Episode Terakhir)" and "Rata-rata Langkah (50 Episode Terakhir)" display the average reward and steps over the last 50 training episodes, giving an indication of learning progress.

5.  **View the Best Path:** After 100 training episodes, the "Start Learning" button will change to "Learning Finished". The maze will then display the best path found by the NPC in yellow. Information about the best episode (based on the highest total reward achieved) will also be shown below the statistics.

## How the Project Works

1.  **Maze Generation:** At the start of each learning session, a 10x10 maze with random obstacles is generated. The 'S' marks the starting position (0, 0), and 'F' marks the goal position (9, 9).

2.  **Q-Learning Algorithm:** The NPC learns to navigate the maze using the Q-learning algorithm, a type of reinforcement learning:
    * **States:** The NPC's position (row and column) in the maze.
    * **Actions:** The possible movements the NPC can take (up, down, left, right).
    * **Rewards:** The NPC receives rewards for its actions:
        * A small negative reward (-0.1) for each step taken to encourage finding the shortest path.
        * A large positive reward (+10) for reaching the goal ('F').
        * A negative reward (-1) for hitting a wall ('#') or making an invalid move.
    * **Q-Table:** The NPC maintains a Q-table, which stores the expected future reward for taking a specific action from a specific state. Initially, all Q-values are zero.
    * **Exploration vs. Exploitation (Epsilon-Greedy):** During training, the NPC uses an epsilon-greedy strategy. With a probability of epsilon, it explores the maze by taking random actions. With a probability of 1-epsilon, it exploits its learned knowledge by choosing the action with the highest Q-value for the current state. Epsilon decreases over time to favor exploitation as the NPC learns.
    * **Q-Value Updates:** After each action, the Q-value for the previous state-action pair is updated based on the reward received and the maximum Q-value of the new state.

3.  **Learning Process:**
    * The NPC goes through 100 episodes of exploring the maze.
    * In each episode, the NPC starts at 'S' and tries to reach 'F'.
    * It takes actions, receives rewards, and updates its Q-table.
    * Over time, the Q-values for actions that lead to the goal will increase, and the NPC will learn the optimal policy (strategy) to reach the goal quickly.

4.  **Finding the Best Path:** After the training is complete, the `findBestPath()` function uses the learned Q-table to determine the shortest path from 'S' to 'F' by always choosing the action with the highest Q-value at each step.

5.  **Visualization:** The HTML, CSS, and JavaScript work together to display the maze and the NPC's movement during training. The best path found after training is highlighted in yellow. The statistics displayed provide insights into the learning progress of the NPC.

example visualisation : 
