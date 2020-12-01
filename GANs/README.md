# GANs from scratch
Explore and implement GAN.

REF :
[Deep Learning : Advanced Computer Vision | Udemy](https://www.udemy.com/course/advanced-computer-vision/) 

GANs are system of two Neural Networks : Generator and Discriminator.

Eg: In case of Deep Fake, Generator generates fake images and discriminator detects if the image is real or not.

Random Noise as i/p to Generator. 

Loss function in case of GANs? As it is also two Neural Networks, we'll have two losses.
For Discriminator, correct loss is Binary cross entropy as it detects real/ fake.
For Generator, loss function is still the same which is Binary Cross entropy.Since it is generating fake images, 
the output is one if the image generated is fake. Here Discriminator weights are frozen.

Noise -> Generator -> Fake Image -> Discriminator -> 1/0

I/p to generator is random noise - a random vector and generator maps this vector to an image.

## Pseudocode of GANs

1. Load in the data: x,y = get_mnist()

2. Create networks.

d = Model(image, prediction)

d.compile(loss='binary_cross_entropy',..) # 1 for real, 0 for fake.

g = Model(noise, image)

3. Combine 'd' and 'g'

fake_prediction = d(g(noise))

combined_model = Model(noise, fake_prediction)

combined_model.compile(loss='binary_cross_entropy', ..) # 1 is always the target

4. Gradient Descent loop,

We train discriminator and generator alternatively inside the loop.

To train the discriminator, we grab random samples of images from our dataset and random samples of images from our 
generator. Then we do one iteration of gradient descent (for both real and fake images)

Then for generator training, we do the following:
First generate batch of noise samples. Then we train the combined model passing in the noise and ones as the target

for epoch in epochs:
    #train discriminator
    real_images = sample from x
    fake_images = g.predict(noise)
    d.train_on_batch(real_images, ones)
    d.train_on_batch(real_images, zeros)
    # train generator
    combined_model.train_on_batch(noise, ones)
    
After several thousand iterations, the generator should be good enough to generate images like mnist dataset.


Loss of both generator and discriminator improves at the same rate.





Mainly using [tensorflow](https://www.tensorflow.org/tutorials/quickstart/advanced) for all applications.

```bash
pip install tensorflow==2.1
```