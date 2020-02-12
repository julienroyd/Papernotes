# Generative Adversarial Imitation Learning (GAIL)
#### Ho, Ermon (2019)

In this work, the authors present a new imitation learning algorithm that allows to learn a policy from expert samples only (without access to the expert policy) that is very similar to the GAN framework wildly used for unsupervised generative tasks.

**Imitation Learning**: The problem of learning to perform a task from expert demonstrations.

### Why it is interesting

If only provided with expert samples (not necessarily full trajectories) and no reward signal, more traditional approaches would be:

* **Behavioral Cloning**: Directly learns to output the same actions as the expert from the corresponding states using supervised learning. This method tends to require a large amount of expert data.
* **Inverse RL followed by RL**: IRL is tasked with finding a cost function under which the expert is uniquely optimal, which is afterwards used to train a new agent using reinforcement learning on that learned cost function. This method is inherently expensive as it solves an RL task repeatedly in its inner loop. 

GAIL instead allows to *directly* learn a policy from expert data, with no middle-step. It does so by replacing the generator in the GAN framework with an RL-agent which is trained to fit distributions of states and actions that define the expert's behavior. The discriminator is trained to guess if the state-action sample comes from the agent's or expert's distribution.

### Theoretical contributions

The authors define a general view of the IRL procedure that include a regulariser \psi from which IRL can be seen as a dual optimisation procedure of an occupancy measure matching problem. They show that different choices of \psi lead to different previously known imitation learning algorithms:

* a constant regulariser \psi leads to exact occupancy measure matching (impractical in practice)
* infinite regulariser for cost functions outside a pre-defined family leads to entropy-regularized apprenticeship learning

### Algorithm

From that regularized IRL framework, they derive GAIL. The cost function is given by:

![](gail_objective.png)

GAIL alternates Agent and Discriminator learning steps:
* **Discriminator**: Adam gradient step to *increase* the cost function w.r.t to D 
* **Agent**: TRPO step to *decrease* the cost function w.r.t to \pi

### Experiments

They evaluate GAIL against three baselines: (1) Behavioral Cloning (BC), (2) Feature Expectation Matching (FEM) and (3) Game-Theoretic Apprenticeship Learning (GTAL) on both classical RL problems (Cartpole, Acrobot, Mountain-Car) and MuJoCo environments (Hopper, Walker, Ant, Humanoid).

They find out that GAIL seem sample efficient in the sense of the amount of expert data needed to learn a good policy, but does require a lot of passes over that data to learn its policy. They believe that its overall data efficiency could be improved by initializing the agent to the policy found by behavioral cloning, which is faster to train as it does not require interactions with the environment.
