# Code Repository

### __"Myofibril and mitochondria morphogenesis are coordinated by a mechanical feedback mechanism in muscle"__
#### Jérôme Avellaneda, Clément Rodier, Fabrice Daian, Thomas Rival, Nuno Luis Miguel, Franck Schnorrer

Preprint : https://www.biorxiv.org/content/10.1101/2020.07.18.209957v1

doi: https://doi.org/10.1101/2020.07.18.209957

## 1 - Setup

First, you need to setup a Python Anaconda environment (https://www.anaconda.com/products/individual) or miniconda, and clone this repository on your computer.

Then process to the python requirements install by typing into the cloned repository on your computer
```
pip install -r requirements.txt
```

This repository contains two main directories:
- *__Segmentation__* which contains scripts for addressing the training and deployment of the segmentation model
- *__Analysis__* which contains script for the shape analysis and paper's figure generation

Install time: Depends mainly of your internet connection as every Python packages are downloaded and installed on the fly.

## 2 - Segmentation (Deep Learning)

### Datasets & Models

All datasets used to train our deep learning segmentation models as well as trained models are provided to download in the table below:

|                |   Links  |
|----------------|----------|
| Datasets       | [link](https://amubox.univ-amu.fr/s/cwa5KfPLxGWXCm4/download) |
| Models         | [link](https://amubox.univ-amu.fr/s/pBSFKic6qASHyJT/download) |

To deploy both Datasets and Models, just unzip the files into the *Segmentation* directory.

Once done you should have a new __data__ directory into the __Segmentation__ directory : Segmentation/data/

and a new __model__ directory into the __Segmentation__ directory : Segmentation/models/



### Model Training & Segmentation

- To train a model from scratch,use the *Segmentation/model_training.ipynb* Jupyter Notebook (See the notebook for detailed step by step instructions)

- To segment an image using a trained model, use *Segmentation/segmentation.ipynb* Jupyter Notebook (See the notebook for detailed step by step instructions)

### Hardware

All models (provided in the link above) have been trained using one Nvidia GV100 GPU card (32Go GPU RAM). 

Training time should vary greatly according to the hardware used (GPU, CPU), but you can build a model on both architecture.

According to your hardware specifications, you should consider decreasing the training *batch size* to avoid GPU/CPU RAM crashes.


## 3 - Analysis : Shape classification and quantification

Once the segmentation is done, the segmentation result is passed to Fiji's MorpholibJ plugin to further post processing and 3D component labelling of objects (See paper Material & Methods section for more details).

A CSV file is generated and passed to the *Analysis/analysis.ipynb* where all shape classification and quantification are done and Figures are generated.

Running time : This notebook can be fully executed in a couple of minuts on a normal computer.



