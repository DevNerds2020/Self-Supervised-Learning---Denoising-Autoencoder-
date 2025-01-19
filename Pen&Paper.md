# Questions and Answers
## 1. VAE vs. Diffusion Models

### Similarities:
1. Both diffusion models and VAEs utilize variational inference as a foundation for their training. In VAEs, the objective is to minimize the negative Evidence Lower Bound (ELBO), which includes a KL-divergence term to align the approximate posterior with the prior distribution. While diffusion models are also based on probabilistic principles and their loss functions are derived from variational bounds, they typically optimize a simplified objective, often equivalent to minimizing the mean squared error between predicted and actual noise at each timestep of the reverse diffusion process. Both approaches share a probabilistic foundation for learning a distribution over the data.

2. Both VAEs and diffusion models involve sampling from Gaussian distributions:
- **VAEs**: The latent variable \( z \) is sampled from a Gaussian distribution.
- **Diffusion Models**: Gaussian noise is added to the data during the forward process, and the reverse process iteratively samples from conditional Gaussian distributions to denoise the data.

This shared reliance on Gaussian distributions highlights the probabilistic nature of both models and their use of Gaussian assumptions to model uncertainty and noise.

3. We can say both of the models are Generative Models.

### Differences:

1. VAEs rely on probabilistic latent variable models and use an encoder-decoder architecture to map data into a latent space, where the latent variables follow a predefined distribution (commonly Gaussian). Diffusion models, on the other hand, progressively add noise (like Gaussian noise) to the data over a series of steps during the forward process, effectively transforming the data into pure noise. The reverse process involves step-by-step denoising to recover the original data.

2. The architectures of VAEs and diffusion models differ. VAEs are based on autoencoders, consisting of an encoder and a decoder that samples from a latent space. Diffusion models commonly employ U-Net architectures, which are well-suited for processing data at multiple scales, although other architectures can also be used.

<img src="unet.png">
<img src="vae.png">

3. The inherent design of VAEs, with its information bottleneck and smoothing effect, leads to blurry and less realistic results. Diffusion models, by learning to reverse a noise process, can generate much higher-quality and more realistic images. This difference in image quality is a significant factor in the increasing popularity of diffusion models for generative tasks.

## 2. Dequantization
Dequantization is a technique used to transform discrete data into a continuous space by adding random noise. For example, pixel values in images are often discrete integers (e.g., 0–255). Dequantization adds small noise to these values, creating a continuous range. This process allows models to work with a continuous probability density function, which is crucial for effective training in generative models like VAEs or flow-based models.


