# A Connection between Generative Adversarial Networks, Inverse Reinforcement Learning, and Energy-Based Models
#### Finn et al. (2016)

In this work, the authors highlight a connection between the GAN training problem and the Max-Entropy Inverse RL problem. By restricting the generator to any model-class for which we can evaluate the density, they formulate the discriminator in a way that requires only estimating the true data distribution, and model this distribution using a Boltzman energy-model (as is used in MaxEnt IRL). They then use this setting to show that:

1. The value of Z which minimizes the discriminator's loss is an importance-sampling estimator of the partition function
2. For this value of Z, the derivative of the discriminator's loss w.r.t the model's parameters is equal to the derivative of the MaxEnt IRL objective
3. The generator's loss is exactly equal to the MaxEnt policy loss

Together, these facts imply that GANs optimise the MaxEnt problem.
