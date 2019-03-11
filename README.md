# A Task of Face Generation
Lower-Half Face Generation conditioned on a given upper-half face picture
## The training data set
Around 10000 set of faces of celebrities are used for the training. Those are preprocessed data initially copied from open-source data set for celebrities all over the world.
## The model architecture in the training phase
CNN-based CVAE (conditional variational auto-encoder) will be trained by the following steps:
1. VAE CNN Encoding: a lower-half face is converted with a simple CNN into a certain vector.
2. Condition: we add the corresponding upper-half face as a "condition" into the above VAE architecture. The above upper-half face is first encoded to a certain vector (using CNN), then is concatenated to the one of the VAE.
3. Gaussian Latent Vector: apply a MLP into the corresponding gaussian variables (latent vector).
5. Decoding (Generation): first concatenate the gaussian vector to the above encoded vector of the input condition. Next, deconvolute the concatanated vector into a picture in the original size.
6. Bernoulli distribution: used to define a probability of having the generated picture.
# The Generation of a Lower-Half Face conditioned on an Upper-Half Face
Given the input upper-half face and the input latent vector, the trained CVAE generates a lower-half face the algorithm thinks "suitable" to the input upper-half in the "style" fully specified by the latent vector.
