# Cat_Face_Generator
This repository generates new cat faces with the help of the PyTorch tutorial and the paper by Radford, Metz, and Chintala(2015) called: "Unsupervised Representation Learning With Deep Convolutional Generative Adversarial Networks.
https://arxiv.org/abs/1511.06434


# Model Architecture (p. 3-4):

While earlier approaches used maxpooling layers the convolutional net of the DCGAN makes use of strided convolutions which enables the network to learn its own spatial downsampling.

The Batch Normalization used after each ConvTranspose2d and Conv2d layer, except for the first Conv2d in the Discriminator and the last ConvTranspose2d layer in the Generator, helps to stabalize learning by normalizing the input to each unit to have zero mean and unit variance. This method allows for better gradient flow in deeper models and minimizes the problems that arise due to poor initialization. Furthermore Batch Normalization helps with preventing the Generator from collapsing all samples to a single point.

The Generator uses the ReLU activation function except for the output layer which is followed by a Tanh function (while no preprocessing is done images are scaled to the range of the tanh activation function which is [-1,1]). On the other hand, the Discriminator uses a leaky ReLU function with the slope of the leak being 0.2.

The Optimizer will be Adam, and the researchers decided on a learning rate of 0.0002 because of 0.0001 being too high. Furthermore the momentum term beta1 is 0.5 as the suggested value of 0.9 resulted in instability while training.


# Example batch of fake cat faces after 100 Epochs
![fake_cats](https://user-images.githubusercontent.com/60868520/95565135-b54d2b80-0a5a-11eb-8978-e8edeaed5d82.png)
