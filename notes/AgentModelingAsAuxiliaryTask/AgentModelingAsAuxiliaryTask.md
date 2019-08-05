# Agent Modeling as Auxiliary Task for Deep Reinforcement Learning
#### Hernandez-Leal, Kartal, Taylor (2019)

In this work, the authors propose a representation learning approach to improve performance in multi-agent RL by teaching the agent to model its opponent/teammate's policy, an auxiliary task referred to as *agent modeling*.

![environmentsAndResults](fig1.png)

They argue that agent modelling usually serve two purposes:
* Cooperative scenario: Improving the coordination efficiency
* Competitive scenario: Helping to better repond to the predicted opponent behavior

They propose two architectures. The first one, *Agent Modeling by parameter Sharing* (AMS-A3C) directly predict the other agent's action by adding an additional head to the network, sharing all previous layers with the policy and value function heads. The second one, *Agent Modeling by policy Features* (AMF-A3C). The agents are trained on pixels on two different discrete control problems. Their results show better performances by both of their approaches than the A3C baseline.

Note that their experiment focus on multi-agent scenarios where only one of the two agents is learning, setting aside the multi-agent non-stationarity problem, an important complication of the multi-agent setup that states that the environment becomes non-stationary from any agent's perspective because of the changing behavior of the other agents in its environment. Therefore, their experimental setup can be seen as a single agent problem as other interactors are fixed and can simply be considered part of the environment.
