# Attention-IQL vs IQL on Maze Offline RL

This notebook provides an implementation and comparative analysis of two offline Reinforcement Learning (RL) algorithms, **Implicit Q-Learning (IQL)** and **Attention-based Implicit Q-Learning (Attention-IQL)**, within various maze environments.

## Overview

The primary goal of this study is to evaluate how IQL and Attention-IQL perform in mazes of increasing complexity, particularly focusing on their ability to learn effective policies from static, offline datasets. The notebook also includes visualizations for value propagation and a detailed comparison of their success rates and average returns.

## Key Features

- **Maze Environment:** A custom `MazeEnv` class supporting various layouts and complexities.
- **Dataset Generation:** Creation of offline datasets comprising expert, medium, and random trajectories.
- **IQL Implementation:** Standard Implicit Q-Learning for policy and value estimation.
- **Attention-IQL Implementation:** A transformer-based variant of IQL that leverages attention mechanisms for state representation, particularly useful for sequential data.
- **Value Heatmaps:** Visualization of learned value functions across the maze for both models.
- **Policy Evaluation:** Metrics including Success Rate (SR) and average return for evaluating learned policies.

## Maze Environments

The notebook evaluates models across four distinct maze environments:

1.  **Original Maze (9x9, Simpler):** A basic maze with a straightforward path to the goal.
2.  **MazeEnv2 (9x9, Slightly More Complex):** Introduces more walls and requires slightly more intricate navigation.
3.  **MazeEnv3 (12x12, Moderately Complex):** A larger maze with a more challenging layout.
4.  **MazeEnv4 (17x17, Highly Complex):** The largest and most complex maze, designed to push the limits of the models.

## Results and Key Takeaways

The study reveals the following key insights from comparing Standard IQL and Attention-IQL:

### Original Maze (9x9, Simpler)
*   **Standard IQL:** Achieved a **1.00 Success Rate (SR)** and a **95.00 average return**. The model successfully learned an optimal policy.
*   **Attention-IQL:** Achieved a **1.00 Success Rate (SR)** and a **95.00 average return**. Performed comparably to Standard IQL, also learning an optimal policy.

### More Complex Mazes (MazeEnv2, MazeEnv3, MazeEnv4)
*   **Increasing Complexity Reveals Limitations:** As the maze environments became more complex (MazeEnv2, MazeEnv3, MazeEnv4), both models' performance degraded significantly. In these challenging environments, **neither Standard IQL nor Attention-IQL achieved any successful trajectories (0.00 SR)**.
*   **Attention-IQL's Marginal Edge:** Despite failing to achieve successful task completion in complex mazes, **Attention-IQL consistently showed a slightly higher average return compared to Standard IQL** in these scenarios. This suggests that the attention mechanism *might* allow it to extract slightly more useful information from state sequences, though not enough to overcome the inherent challenges of offline RL in highly complex, underrepresented environments.

## Conclusion

For simpler maze configurations, both Standard IQL and Attention-IQL are capable of achieving optimal performance. However, as environment complexity increases, the limitations of both models become apparent. The results highlight the significant challenges of offline reinforcement learning in complex environments, particularly when the offline dataset may not sufficiently cover optimal trajectories. While Attention-IQL showed a marginal improvement in average return in harder mazes, this advantage was not significant enough to lead to successful policy learning.

## Further Research

To address the observed limitations, future work could explore:

*   **Larger and more diverse datasets:** To provide better coverage of optimal trajectories in complex mazes.
*   **Improved model architectures:** Investigating more advanced sequence modeling or hierarchical approaches for robust state representation.
