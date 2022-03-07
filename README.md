# neural_populations
Repository for semester project at The Cortical Computation Group, INI, UZH/ETH, modeling neural populations.

## Thoery about K-means and the EM algorithm
### GMM
* GBC in which we dont have the labels. The probabilistic model is the same. We have some labels that follow an underlying categorical distribution, but we dont observe them like in GBC. This leads us to treat the modls differently but underneatht hey look a lot a like. 
* The objective function is now non convex but we can sole using ther EM algorithm.

### Hard EM
1. Init parameters ($\Sigma$, $\mu$, $w$)
2. For a finite number of steps
	1. Predict the moslt likely class for each data point 
	2. Compute the MLE as for a GBC. We use the parameters to run the next step. 

* We have hard assigments enven thought we might be very uncertain about the assigments (one underlying gaussian) overlaping clusrters in solution.

### Soft EM
* Same same but now we assign priobabilities to the indenity of each point to a cluster.
* This means inferring distributions over latent (hidden) variables z
* Suppose we’re given a model of the labels given the parameters and the data given the labels.
* Then, for each data point, we can compute a posterior distribution over cluster membership

### EM details
* Constrained versions. Take covariance matrices: spherical, diagonal, full, tied. 
* Initialization: uniform weights, means, empirical covariance data
* GNN vs K-means: k means is hard EM GMM where uniform weights are 1/k the number of clusters and spherical covariaces. Alternatively it can be seen as doft EM where the variances shrink to 0.
 
---

## What do we know
- online k-means can be seen as an instance of 'Winner takes it all' where centroids are neurons and the data points are stimulus. Each time a new stimulus is presented only the most adjacent neuron (centroid) is updated, and is hence the winner. We would like tom implement a soft WTA, where given an input not only one neuron gets activated but rather a subset of the neurons but specially the ones that are tuned to thin input. 
- This WTA-k_means procedure can represent a population of neurons that all recive the same input and have an inhibitory connection to every other neuron in the population (including itslef but not enough to inhibit activation, once activated). In a sense one could say that neurons are competing for the stimulus, becasue onece one of them becomes activated it inhibits the others and at the same time the winning neuron strengthens its connection via Hebbian learning.
- I guess in a way we are learning the tunning of the neurons but its not like we have a loss function, this is why it can be analogous to a unsupervised learning algorithm. 

## The network model
- we have two input populations that are fully connected to a third population. The weights between members of this populations is initialized at random. Esencially like the input layer and the first layer of a ANN, where the first layer is the third popuilation and the input layer is the first and the second population conbined (one can make it so that the inputs of the first and second population come from differen distributions).
- Lets call population 1: $x_1$, population 2: $x_2$ and population 3: $z$, and maybe a read out population $y$.
- But all of the above is for a network view
- We rather do thinks in the clustering way. 
- The inputs then become the datapoints that are subsequently added to the network, in which half of the coordinates are drawn from on distribution and the other half are drawn from another dist. 

---

## Questions
- How can homeostasis be represented in such a model -> It was something like allowing centroids/neurons to nudge in a certain direction, where the degree of the nunge would be determined by the basline activity of a specific neuron. 
- Im getting confused with the representation. In the network model the input is actually as set of reals that go from the input units to each of the units in the $z$ population. But in the clustering framework the input is only one real that varies accoriding to a Gaussian distribution (whose parameters we want to inferre). **How are these two views reconciled??**

---

## TODO
- Reconcile dimensions contradiction in the network and clusterin view. 
- Maybe rewatch the GMM and EM algorith lectures from IML.
