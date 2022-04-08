# neural_populations
Repository for semester project at The Cortical Computation Group, INI, UZH/ETH, modeling neural populations.

## TODO
- Finish reading the papers
	- [x] A method to add GMMs (via a weithed sum of the parameters of the components). 
	- [x][x] Methods to do online learnign with GMM
- Decide if the proposed GMM online algorithms are a good fit for our ANN model. 
	- They are not. They concentrate on the adjustment of the number of components in the GMM. In our case this would be fixed since they rpresent the neurons which cannot simplye appear or disappear. Perhaps a simple online GMM will sufice for a modle like ours to work.  
- Get the code started (from the IML 2021 demos?)
	- Eventually you will get the problem of having a shit ton of neurons and few data points, we will see what happend. 
	- When there rmember to se `scikitlearn` documentation regardin the degeneracy (perhaps it is the same degeneracy that Krause mentioned in the IML lecutres).

## Outline of the code
+ Sturcture the whole thing as a story. Intoduce the hard EM then explain what it has to do with a toy NN (WTA netwk). Then maybe delve into why the EM algorithm is a good idea to model this system. Then go on to relax the simplification in the model explaing what the implications would be for of toy neural system. 

* first demo with K-means, show how some centroids do not get updated given the update rule, e.g only the closest point gets updated, which is saying that only one neuron gets activated and therofere only one neuron changes its weights (e.g meoves it centroid coordinates). 
* then demo with gaussian mixute model. two important features.
	* cluster weighst can vary which encode the posibility that a random data points belongs to a certain clustrer. this could be a way in which we can a priori encode the activity level of neurons.
	* since now we are dealing with soft assignment of clustrer membership, all neurons get updated at each step, and therofre we dont have "dead neurons".