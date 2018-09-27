# DeepMimic: Example-Guided Deep Reinforcement Learning of Physics-Based Character Skills

#### Peng, Abbeel, Levine, Van de Panne (2018)

In this work, the authors combine reinforcement learning with imitation learning to train policies that can control various physics based characters to perform different motions in a natural fashion while having the capacity to tweak their movement to accomplish tasks like kicking a target, avoiding obstacles or recovering from perturbations.

They provide "a framework for physics-based character animation that combines goal-directed reinforcement learning with data". The use of data offers an alternative to the difficult task of specifying a reward function for natural movement.

* **states**: concatenation of every joint relative position to the root, joint angles (quaternions), root position, joint positional and angular velocities, a *phase variable* indicating where we are at in the provided example-motion and finally a *goal* if the agent is performing a task (could be the position of the target, the direction to follow, etc.).
* **actions**: defined as angular shifts and an external PD-controller translates them into torques applied to the simulated character (which could explain why they don't use supervised learning to train the model for motion-imitation).
* **transitions**: they use a simulator called *Bullet* to detect collisions, apply motion etc. in their physical world. The policy is queried at 30Hz while the physics simulator runs at 1200Hz.
* **rewards**: they combine two sources of reward to train the agent, a motion-imitation reward and a task-specific reward. The first one is computed by measuring some positional and angular offset as well as velocity differences between the controlled character and the provided motion data. The second is a more classic reward that we would see in RL tasks (rewards if the agent touches the target, etc.).

![fig1](fig1.PNG)


### Training
* They train two networks (Actor-Critic). The actor is trained off-policy using Proximal Policy Optimization (PPO) while the critic models the state-value function V(s) and is trained off-policy (*I think*) with the TD-lambda algorithm. Advantages are computed using the approximated V(s) and the lambda-Return (generalized advantage estimator or GAE).
* Takes about 2 days of training per motion/task. Everything is run on CPU

### Exploration tricks
* **Reference state initialization:** Initialize the episode at different frame of the provided example-motion. This proved important to learn motions where some states are difficult to reach (like backflip).
* **Early Termination:** Stops the episode when huge fail occurs (like falling down). This prevents the agent of sacrificing capacity to learn to reach local minima by trying to perform a flip while laying on the ground.

### Multi-skill integration
* **Multi-clip reward:** Here they simply use multiple example-motions and take the *max* over the corresponding imitation-rewards as the current-step imitation-reward. This is a step-wise multi-motion technique, appropriate for similar motions (types of walk).
* **Skill selector:** Train a single policy that receives a one-hot vector indicating the task (motion) to try to fit. The agent performs this motion for one complete cycle, during which the imitation-reward is the one corresponding to the selected motion. Once trained, a user could specify (with a controller) which motion to perform. This is a cycle-wise multi-motion technique, appropriate for very different motions (types of jump). 
* **Composite policy:** Train several policies, each of which are specialized to a specific motion. The actions performed are a weighted average of actions sampled from all those policies. The weights are computed using a Boltzman distribution (softmax with a temperature parameter) over all approximate state values.

### Robustness and Retargeting
* **Character retargeting:** They show that their method is robust enough to allow a different character (like a humanoid or a model of Atlas) to learn to perform a motion from the same target frames.
* **Environment retargeting:** They learn for example a landing motion, performed in MOCAP on flat terrain, and are able to use this learned motion to land after a 2 meters fall (which shows that the learned policy is still robust in different use-case).
* **Physical retargetting:** They change the gravity strength and show robustness of their policies for such environmental changes.
* **Robustness to perturbations:** Finally their trained agents are also robust to the application of perturbation forces. This property is expected to come from the noise exploration process during training.

### Other perks of the paper

* Clear and concise explanations of Off-Policy Policy Gradient, TD-lambda and PPO
* Good accompanying video

![fig2](fig2.PNG)
![fig3](fig3.PNG)
