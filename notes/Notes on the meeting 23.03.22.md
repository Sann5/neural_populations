# Notes on the meeting 23.03.22
### about the representation of the dimensions in the k-means setting
* We can either have each dimension represent an input neuron or...
* have each diemsnion be a population of neurons that toghether encode a specific value. 

### on the issue of analgoy between WTA and k-means (normalization)
* in cartesian space the cordinates of a centroid are not analogous to the weights between the input population and a specific neuron (in the scenario where each dimension is a population its not even clear what the corrdinates would represent). 
* apparently if one normalizes the weight and the inputs then everything lies ina sphere and then it works out, meaning thet the centroid that is closes to a specific data point is also the one that has maximally the largest output in a WTA network. 

### about homogeneity
* We would like for all the neurons to be used. 
* However, naturally all neurons wont be used for a specific input pattern. There shoulsd still be no free loading neurons.
* We can ecnode the the base rate as the weight of the linear combination of the gaussians and have this weight be modified through time when a specific neuron hasent been stimulated in some time. However this thresholds should be robust in the sense that it should be patient in that it shouldnt het kicked if its falling sasleep just becasue there has been a couple inputs that dont stimulate it. 
* There was mention of experiemntal evidence of this happening, where the neuron was kicked after some time, then it wakes uop and kinda finds its a stimulus to respond to. 
* there was also mention of experimental evidence that different neurons have different baseline activitis that follow a log normal distribution (one could pontetnially also model this as a gamma distribution). we could initialize the wieghts of the gaussina mixture by drawing values from thsi gaussian an then nomralizing in order to get the baeline acitivites. 

### Additional notes
* it seems that one could model the baseline activity separatly of the kicking function fo falling-asleep neurons. the baseline activity as the weight intialization and the kickin function as some aditional update to the centroids every time a certain condition is fullfiled. 
* interesting point aboout soft EM for probability of belonging to a class allows for cluster overlapp, or in other words for two neurons to identically represent the same cluster. this could be a feature that conveys rubusteness to the system.
* interesting question about how the usual way to think about GMM applies to this problem. rather than interested in clustering the data and finding out the procces though which its generated (the statistics of the gausian proces that generates it), we would be interested in training a system that lerns to represent a families of signals (inputs) that is hopefully well characterized by a Gaussian? 