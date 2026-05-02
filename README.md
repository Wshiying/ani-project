# Using ANI to Predict Molecular Energies

## Project Overview

This project uses an ANI-style atomic neural network model to predict molecular energies from molecular structures. The model is implemented using TorchANI and PyTorch.

ANI models convert molecular geometries into atomic environment vectors (AEVs). These AEVs describe each atom’s local chemical environment while preserving important physical symmetries such as translation, rotation, and permutation invariance. Separate atomic neural networks are used for H, C, N, and O atoms, and the predicted atomic energy contributions are summed to obtain the total molecular energy.

The goal of this project was to build a complete supervised learning workflow for molecular energy prediction, including data preparation, model construction, hyperparameter tuning, multiple-run testing, cross-validation, and final full-data training.

## Repository Structure

- `data/`: dataset instructions
- `notebooks/`: Jupyter notebooks for Checkpoints 1–5
- `figures/`: plots used in the final report
- `reports/`: final written report

## Checkpoints

- `checkpoint1.ipynb`: Data preparation and setup
- `checkpoint2.ipynb`: Network construction and workflow development
- `checkpoint3.ipynb`: Regularization strategies and hyperparameter tuning
- `checkpoint4.ipynb`: Multiple runs and 5-fold cross-validation
- `checkpoint5.ipynb`: Final training on all available data and comparison to the ANI-1 paper

## Main Results

Best configuration:

- hidden dimension: 64
- learning rate: 1e-3
- L2 regularization: 0
- batch size: 256

Checkpoint 3 held-out test MAE: approximately 1.10 kcal/mol.

Checkpoint 5 final full-data results:

- Full-data MAE: 0.694 kcal/mol
- Full-data RMSE: 0.893 kcal/mol

The Checkpoint 5 result is a full-data fit metric, not a held-out test metric, because the final model was trained on all available data.

## Data

The dataset file `ani_gdb_s01_to_s04.h5` is not included in this repository because it is large and was provided through bCourses.

To run the notebooks, download `ani_gdb_s01_to_s04.h5` from bCourses and place it in the working directory.

## Requirements

Main packages used:

- NumPy
- Pandas
- Matplotlib
- PyTorch
- TorchANI
- scikit-learn
- tqdm
- Jupyter Notebook

## References

Smith, J. S., Isayev, O., & Roitberg, A. E. (2017). ANI-1: An extensible neural network potential with DFT accuracy at force field computational cost. *Chemical Science, 8*, 3192–3203.

Gao, X., Ramezanghorbani, F., Isayev, O., Smith, J. S., & Roitberg, A. E. (2020). TorchANI: A free and open source PyTorch based deep learning implementation of the ANI neural network potentials. *Journal of Chemical Information and Modeling, 60*(7), 3408–3415.

Kingma, D. P., & Ba, J. (2014). Adam: A method for stochastic optimization. arXiv:1412.6980.
