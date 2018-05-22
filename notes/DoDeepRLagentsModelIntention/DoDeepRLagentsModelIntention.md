# De Deep Reinforcement Learning Agents Model Intentions?
#### Martiisen *et al.* (2018)

In this work the authors focus on a single cooperative environment to :

1. Show that the [MADDPG agents](../Multi-AgentActor-CriticforMixedCooperative-CompetitiveEnvironments/Multi-AgentActor-CriticforMixedCooperative-CompetitiveEnvironments.md) learn to model their teamates intentions
2. Propose shuffling the agent's order at each episode to avoid agents overfitting to the behavior of their training teamates (co-adaptation) and therefore allow better performance when teamed with unseen agents

*Motivation* : "Inferring the intentions of others is the basis for effective cooperation"

**Investigation of Intention Modelling**

They verify if the agents trained with MADDPG model other agent's intentions by traning a single read-out linear layer to predict the final landmark of all other agents. They tried to plug this linear-single-layer-predictor to both the input observations, first hidden layer and second hidden layer of the MADDGP agent. They found that the other agent's intentions were best predicted when plugged to the first hidden layer (suggesting that the second hidden layer represents information more specific to the agent's policy and therefore lose information about other's intentions), whereas these intentions *could not* be decoded by a linear predictor when plugged to the input observations (which means that the MADDPG agent made the intentions of its teamates more explicit in its first hidden layer).

**Investigation of Co-adaptation**

They argue that the lack of generalization is a general problem in Reinforcement Learning, and that testing agents in the same environments they were trained in is an important cause. See experiments with *Sheldon* agents.

<center>
<table>
	<tr>
		<td>
			<center>
			<img src="figure1.PNG" width="30%">
			<img src="figure2.PNG" width="55%">
			</center>
		</td>
	</tr>
</table>
</center>
