# Bayesian Action Decoder for Deep Multi-Agent Reinforcement Learning (BAD)
#### Foerster et al. (2019)

In this work, they tackle the problem of discovering effective communication protocols and policies in cooperative, partially observable multi-agent settings. Rather than allowing agents to communicate through *cheap talk* (communication channels that do not affect the state transition distribution), agents are trained to make their actions themselves as communicative as possible and to decode what actions made by other agents mean about their view of the world. So in that framework, all actions are public knowledge (observed by all agents). They call their learning algorithm *Bayesian Action Decoder* (BAD).

### Common Knowledge Framework

In this framwork, some features of the environment are publicly observable and form the common knowledge among agents (every see these features and evryone know that enveryone see these features).

This common knowledge is used to compute a *public belief* over the agents' private features.
