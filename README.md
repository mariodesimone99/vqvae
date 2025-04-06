# VQ-VAE

This project implements **VQ-VAE Model** ([paper link](https://arxiv.org/abs/1711.00937) for the generation of audio samples or changes through conditioning, the voice of an existing one

## Project Structure

The project is made of a all-in-one jupyter notebook file, divided into sections like:
- **

## Datasets

The dataset used is **PASCAL VOC 2008 Attributes** available at the following [Link](https://vision.cs.uiuc.edu/attributes/).

You need to download "aPascal images" and "Annotations".

**NOTE 1**: The training set corresponds to the VOC2008 train set, and the test set corresponds to the VOC2008 validation set.  
**NOTE 2**: If the download link doesn't work, you can use [Wayback Machine](https://web.archive.org/) to retrieve a previous version of the website (e.g., in 2022, the website worked).

After downloading, create a `data/VOC2008_attribute/` folder with the following structure:
- **`ann/`**: Must contain `ann_train.txt` and `ann_val.txt`, which are the annotations of the dataset.
- **`train/`**: Images of the train split.
- **`val/`**: Images of the val/test split.
- **`attribute_names.txt`**: List of attributes for attribute prediction.
- **`class_names.txt`**: List of classes for object detection.

## Installation

### Create Environment

You need to create an environment with the following packages:

```bash
- torch
- torchmetrics
- numpy
- yaml
- wandb
- tqdm
- PIL
- pandas
- matplotlib
- sklearn
- netron
```

### Selective-search Boxes

You have to install selective search package:

```bash 
pip install selective-search
```

and after run **`src/object_detection/selective_search.py`**  in order to create the file containing the proposals boxes.
You will obtain a folder "**`selectivesearch/`**" containing 2 files `.pt`

## Training

The project is split into 3 parts:
- **Single task - Object Detection**
- **Single task - Attribute Prediction**
- **Multi-task - Cross-Stitch Network with the previous 2 tasks**

Once you have selected the task(s) to solve, you can run the corresponding `.sh` file in the `script/` folder. You can edit the corrisponding `.yaml` file in the `config/` folder to change the experiment settings.

After training, a datetime folder will be created in the `experiments/` folder containing the output of the experiment and the model checkpoint (including the best model checkpoint).

## Evaluation

After training your model, you can evaluate it through the`eval.ipynb` notebook corresponding to the chosen experiment. Once you edit the first code block with your model path, you can run all the cells, and the last cells will show the quantitative results.

## Optional - Netron

For each task, you can view the model architecture by running all cells of the corresponding `netron.ipynb` notebook. This generates a `.onnx` file (follow [Netron GitHub](https://github.com/lutzroeder/netron) for details).

## Optional - Qualitative Results

For each task, you can view some qualitative results by running all cells of the corresponding`qualitative_results.ipynb` notebook. The images will be displayed directly in the notebook.
