# Generative Dog Images

**Problem** 
Use GANs to create images of dogs.

**Data**
[Stanford Dogs Dataset](http://vision.stanford.edu/aditya86/ImageNetDogs/)
* **Number of categories:** 120
* **Number of images:** 20,580
* **Annotations:** Class labels, Bounding boxes

**Evaluation**
* **MiFID** (*Memorization-informed Frechet Inception Distance*): Modification from [**FID**](https://arxiv.org/abs/1706.08500) ([github](https://github.com/bioinf-jku/TTUR))
* The smaller, the better.

**Submission**
Generate 10,000 images, PNG format, size 64x64x3 (RGB) ---> zip them.

### 1st place solution

**Preprocessing & Augmentation:**
* use BoundingBox(no modification)
* resize 64 (one size) and then RandomCrop to image size (64,64)
* HorizontalFlip(p=0.5)

**Model:** BigGAN
* parameters G:10M, D:8M
* input noise: normal distribution (nz=120)
* LeakyReLU

**Loss:** BCE loss
**Optimizer:** Adam 
**Batch size:** 32
**Epochs:** 130
**Other models scores:**
* DCGANs: 55
* AC-GAN: 50
* ACGAN-projection: 39
* BigGAN: 31 (best score)

### 2nd place solution

**Model:** BigGAN
* hierarchical latent noise
* projection

**Loss:** RaLS with weighted auxiliay classification loss
**Batch size:** 128

### 3rd place solution

**Preprocessing:** bounding box cropping only
**Loss:** Try many 
* 1st choice: Standard DCGAN
* 2nd choice: LsGAN-with-Sigmoid

**Best approaches**
* **Model:** BigGAN, StyleGAN
* **Downsample/upsample:** Strided Convolutions
* **Activation function:** LeakyReLU
* Batch normalization
* **Optimizer:** AdamSGD
* **Latent space:** Gaussian
* Sperate Batches of Real and Fake Images

### Useful articles:
**GANs roadmap:** https://blog.floydhub.com/gans-story-so-far/
**Text to Image Generation:** https://arxiv.org/abs/1605.05396
**Image to Image Translation:** https://arxiv.org/abs/1611.07004









