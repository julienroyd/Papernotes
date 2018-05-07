# Adversarial Policy Gradient for Alternating Markov Games
#### Gao, Müller, Hayward (2018)

In this paper, the authors conveniently review Markov Decision Processes (MDP) as well as the 2-players variant, Alternating Markov Games (AMG), which include MDP as a special case. Based on the Bellman equations of the latter framework, they suggest two Adversarial Monte-Carlo Policy Gradient algorithms (AMCPG-A and AMCPG-B) for which the core idea is to use a critic that approximates the *minimum* return instead of the *mean* return. The main steps of AMCPG-A are presented are :

1. Run *n* episodes
2. Uniformly sample *n* (s,a) pairs, one from each episode
3. Run *k* rollouts starting from (s,a) for each episode, and keep the minimal return *w* from those rollouts
4. Use *w* as critic value-estimation for this episode

*Note:* The authors suggest using the minimum instead of mean only for AMG and do not metion that this could be helpful for regular MDP.

### Other interesting notions

**Evaluation Procedure** : They evaluate against some benchmark. The interesting aspect is that each evaluation is like a mini-tournament in which they play 5 games starting from all possible opening moves. I think this is a clever way to ensure statistical significance of a win from one of the two agent. The takeaway : when evaluation an agent, (1) evaluate over several games and (2) make sure those different games cover as much as possible of the diversity spectrum.

**Board-size independant Net** : Their architecture receives multiples board size inputs in parallel (not sure exactly how this is implemented). This allows them to train a single model on multiple board sizes and therefre allows the trained model to generalize to different board sizes.
