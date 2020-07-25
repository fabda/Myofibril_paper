# Code Repository

### __"Myofibril and mitochondria morphogenesis are coordinated by a mechanical feedback mechanism in muscle"__
#### Jérôme Avellaneda, Clément Rodier, Fabrice Daian, Thomas Rival, Nuno Luis Miguel, Franck Schnorrer

Preprint : https://www.biorxiv.org/content/10.1101/2020.07.18.209957v1

doi: https://doi.org/10.1101/2020.07.18.209957

## 1 - Setup (with installation on local computer)

First, you need to setup a Python Anaconda environment (https://www.anaconda.com/products/individual) or miniconda (Python 3.5 or higher), and clone this repository on your computer.

Then create a virtual environment and process to the python requirements install by typing into the cloned repository on your computer
```console
pip install -r requirements.txt
```

Then install _ipython kernel_, type:

```console
ipyhton kernel install --user --name=myofibril_kernel
```

and starts Jupyter Notebook server:

```console
jupyter notebook
```

You'll may be have to change the default jupyter notebook kernel to use the __myofibril_kernel__ 

To do so, once your notebook is open, select _Menu Kernel_ -> Change kernel -> myofibril_kernel

This repository contains two main directories:
- *__Segmentation__* which contains scripts for addressing the training and deployment of the segmentation model
- *__Analysis__* which contains script for the shape analysis and paper's figure generation

*__Install time:__* Depends mainly of your internet connection as every Python packages are downloaded and installed on the fly.

## 1 - Alternative Setup with  MyBinder

Click on the button below to deploy a Jupyter Notebook server on the cloud and run the code without any install on a local computer (This could take a couple of minuts)

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/fabda/Myofibril_paper/master)


## 2 - Segmentation (Deep Learning)

### Datasets & Models

All datasets used to train our deep learning segmentation models as well as trained models are provided to download in the table below:

|                |   Links  |
|----------------|----------|
| Datasets       | [link](https://amubox.univ-amu.fr/s/cwa5KfPLxGWXCm4/download) |
| Models         | [link](https://amubox.univ-amu.fr/s/pBSFKic6qASHyJT/download) |

To deploy both Datasets and Models:

a) You can just unzip the files into the *Segmentation* directory.

Once done you should have a new __data__ directory into the __Segmentation__ directory : Segmentation/data/

and a new __model__ directory into the __Segmentation__ directory : Segmentation/models/

b) or you can run the __download_model_and_data.ipynb__ Jupyter Notebook to directly download models and data automatically.

### Model Training & Segmentation

- To train a model from scratch,use the *Segmentation/model_training.ipynb* Jupyter Notebook (See the notebook for detailed step by step instructions)

- To segment an image using a trained model, use *Segmentation/segmentation.ipynb* Jupyter Notebook (See the notebook for detailed step by step instructions)

### Hardware

All models (provided in the link above) have been trained using one Nvidia GV100 GPU card (32Go GPU RAM). 

- Training time should vary greatly according to the hardware used (GPU, CPU), but you can build a model on both architecture even if we advise you to train the model on a GPU card.

- Segmentation can be done on a full 1024x1024 stack in a couple of seconds on a GPU (dozen seconds on a CPU)

According to your hardware specifications, you should also consider decreasing the training *batch size* parameter into the Notebook to avoid GPU/CPU RAM crashes.

Some insight on model training time according to CPU and GPU hardware tested with a fixed 400 steps per epochs parameters:

|     Hardware        |   Time per epoch (in seconds)  |
|----------------|----------|
| Nvidia GV 100  | 27 s     |
| CPU            | 769 s    |



## 3 - Analysis : Shape classification and quantification

Once the segmentation is done, the segmentation result is passed to Fiji's MorpholibJ plugin to further post processing and 3D component labelling of objects (See paper Material & Methods section for more details).

A CSV file is generated and passed to the *Analysis/analysis.ipynb* where all shape classification and quantification are done and Figures are generated.

*__Running time__* : This notebook can be fully executed in a couple of minuts on a normal computer.

## 4 - License
This code repository is release under the [GPL v3.0 License](https://github.com/fabda/Myofibril_paper/blob/master/LICENSE)

