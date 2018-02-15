# Understanding the Difficulty of Training Deep Feedforward Neural Networks
#### Glorot, Bengio (2010)

The authors investigate how bad choice of initialization schemes and activations functions can slow down or prevent learning in deep feedforward networks. They suggest a new initialization scheme that allows to train a deep network end-to-end more effectively without having to use greedy layer-wise pretraining. They experiment on 5 datasets (Shapeset-3x2, MNIST, CIFAR-10, small-ImageNet)

### Activation Functions

* **Sigmoid** : Units of deepest layer quickly saturates and sometimes never escape that regime
	* That happens because early layers randomly initialize do not perform transformations useful to the classification task. Error gradient then tends to push $Wh$ to zero. Once saturated, the gradient cannot backpropagate efficiently anymore. If by luck enough gradient information achieve to make the first layers learn more useful features, then the network can desaturate the last layer and get out from that regime.
	* Might be caused by the fact that weights are initialized centered around zero, while sigmoid's mean isn't zero (it saturates at zero).

* **Tanh** : Units gradually saturate from starting from layer 1 up to deepest layers, as training progresses
	* Happens when weights are initialized with Standard Initialization
	* Why it happens remain to be understood.

* **Softsign** : Observe similar phenomenon than for $tanh$
	* Saturation occurs faster at the beginning but then slows down (probably because $softsign$ approaches its asypmtotes more slowly than $tanh$)
	* A lot fewer units are saturated at the end of training


### Propagation of Gradients

The authors suggest the *Normalized Initialization* as an alternative to the *Standard Initialization* :

$$\text{Standard Initialization : } W \sim U[-\sqrt{\frac{1}{n_j}}, \sqrt{frac{1}{n_j}}]$$

$$\text{Normalized Initialization : } W \sim U[-\sqrt{\frac{6}{n_j + n_{j+1}}}, \sqrt{\frac{6}{n_j + n_{j+1}}}]$$

Normalized Initialization Properties :
* Maintains the variance of forward-propagated activations and back-propagated gradients across layers




<img src="gradients.PNG" width="60%">

### Conclusions
* Bla bla

![demo](demo.PNG)
