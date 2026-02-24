## Author

**Saumya Kumari**  
Roll Number: 102303161  

---

# Learning Probability Density Function Using GAN

## Objective

The objective of this project is to learn the Probability Density Function (PDF) of a transformed random variable using a Generative Adversarial Network (GAN).  

No analytical form of the distribution is assumed.  
The GAN learns the distribution purely from data samples.

---

## Dataset

**Dataset Name:** India Air Quality Data  
**Feature Used:** NO2 Concentration  

Dataset Link:  
https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data

---

## Mathematical Transformation

Each NO2 value `x` is transformed into a new variable `z` using:

```
z = x + a_r sin(b_r x)
```

Where:

- a_r = 0.5 (r mod 7)  
- b_r = 0.3 ((r mod 5) + 1)  
- r = University Roll Number  

For Roll Number **102303161**:

```
a_r = 1.0
b_r = 0.6
```

This transformation introduces a nonlinear perturbation into the original NO2 distribution.

---

## Methodology

### 1. Data Preprocessing
- Extracted NO2 values from the dataset  
- Removed missing values  
- Applied nonlinear transformation to obtain variable `z`  
- Standardized data for stable GAN training  

---

### 2. GAN Architecture

#### Generator Network
- Input: 1D Gaussian noise (N(0,1))  
- Two Hidden Layers  
- Activation: ReLU  
- Output: Generated sample of `z`  

#### Discriminator Network
- Input: Real or Fake `z` sample  
- Two Hidden Layers  
- Activation: ReLU  
- Output: Sigmoid (Real / Fake classification)  

---

### 3. Training Process
- Real Samples: Transformed `z` values  
- Fake Samples: Generated samples from Generator  
- Loss Function: Binary Cross Entropy  
- Optimizer: Adam  
- Adversarial training between Generator and Discriminator  

---

### 4. PDF Estimation
After training:

- Generated 10,000 samples from the Generator  
- Estimated PDF using:
  - Histogram Density Estimation  
  - Kernel Density Estimation (KDE)  

---

## Results

- The GAN successfully captured the dominant mode of the distribution  
- No major mode collapse observed  
- Generated samples reflect right-skewed behavior of air pollution data  
- KDE curve appears smooth and realistic  
- The learned PDF closely matches the transformed data distribution  

---

## Observations

### Mode Coverage
The model captured the primary peak and minor variations without collapsing to a single mode.

### Training Stability
Training remained stable with gradual convergence. Minor oscillations were observed during early epochs.

### Quality of Generated Distribution
The generated distribution shows realistic skewness and smooth density approximation.

---

## Conclusion

This project demonstrates that a GAN can learn an unknown probability density function purely from data without assuming any parametric distribution (such as Gaussian or Exponential).

The approach is flexible and scalable to higher dimensional distributions.
