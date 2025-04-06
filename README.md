# VQ-VAE

This project implements **VQ-VAE Model** ([Neural Discrete Learning](https://arxiv.org/abs/1711.00937)) for the generation of audio samples or changes through conditioning, the voice of an existing one

## Project Structure

The project is made of a all-in-one jupyter notebook file, divided into sections like:
- **Hyperparameters**: chosen according to the paper
- **Dataset**: VCTK preprocessed to be used according to our goals
- **Model Definition**: VQ and WaveNet modules
- **Model Training and Samples Generation**
