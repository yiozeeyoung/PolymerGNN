# PolymerGNN
<img src="https://github.com/owencqueen/PolymerGNN/blob/main/img/whole_arch.jpg" data-canonical-src="https://github.com/owencqueen/PolymerGNN/blob/main/img/whole_arch.jpg" width="700" height="700" />

## About This Repository

This repository contains Graph Neural Networks (GNNs) for polymer property prediction, originally developed by Queen et al. The models are designed to predict various polymer properties including glass transition temperature (Tg) and intrinsic viscosity (IV) using molecular graph representations. The work is published in Nature npj Computational Materials: <a href='https://www.nature.com/articles/s41524-023-01034-3/'>Paper</a>

### Key Features:
- **Multi-task learning**: Joint prediction of multiple polymer properties
- **Graph neural networks**: Leverages molecular structure through graph representations
- **Explainability tools**: Integrated tools for model interpretation
- **Cross-validation support**: Robust model evaluation capabilities

## Modifications in This Fork

This fork includes the following updates to ensure compatibility with current PyTorch and PyTorch Geometric versions:

- **Fixed deprecated syntax in PolymerGNN_Tg model**: Updated outdated PyTorch Geometric operations to ensure the model runs correctly with modern library versions
- **Syntax updates**: Resolved compatibility issues that prevented the original model from running
- **Maintained backward compatibility**: All original functionality preserved while fixing runtime issues

The core algorithms and model architectures remain unchanged from the original implementation.

## PolymerLearn Package Structure
`polymerlearn` is the main component of the repository. This contains all of the driver code for `PolymerGNN`, explainability tools, and utilities for proprocessing data in the format provided.

```
polymerlearn
├── __init__.py
├── explain
│   ├── __init__.py
│   ├── custom_gcam.py
│   ├── explain_gnn.py
│   └── modified_gnns.py
├── models
│   └── gnn
│       ├── __init__.py
│       ├── iv.py
│       ├── iv_evidential.py
│       ├── joint.py
│       └── tg.py
└── utils
    ├── __init__.py
    ├── graph_prep.py
    ├── losses.py
    ├── train_evidential.py
    ├── train_graphs.py
    ├── uncertainty.py
    └── xyz2mol.py
```

## Setting up the Environment

### Development Environment
**This fork has been developed and tested on macOS with Python 3.10+**. The requirements.txt file is optimized for macOS systems.

### Platform-Specific Installation

#### For macOS (Recommended):
1. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate
```

2. Install requirements:
```bash
pip install -r requirements.txt
```

3. Install the polymerlearn package:
```bash
pip install -e .
```

#### For Windows:
⚠️ **Important**: Windows users need to install PyTorch separately before installing other requirements, as the PyTorch installation may differ based on your system configuration (CPU vs GPU, CUDA version, etc.).

1. First install PyTorch following the official instructions at [pytorch.org](https://pytorch.org/)
2. Then install PyTorch Geometric following [PyG installation guide](https://pytorch-geometric.readthedocs.io/en/latest/install/installation.html)
3. Finally install remaining requirements:
```bash
pip install -r requirements.txt
```

#### For Linux:
Similar to Windows, you may need to install PyTorch and PyTorch Geometric separately based on your system configuration.

### Legacy Installation (Original Method)
If you use Anaconda, you can set up all the requirements from the yml file:
```
conda env create --name your_env_name --file polymergnn_env.yml
```
This sets up all of the packages, and Owen has verified that it can be used on the ISAAC cluster.

For more general setup instructions for external packages, please reference [conda-instructions.md](https://github.com/owencqueen/PolymerGNN/blob/main/conda-instructions.md).

### Requirements
- Python 3.8+ (tested with Python 3.10)
- PyTorch 2.0+
- PyTorch Geometric 2.4+
- See `requirements.txt` for complete list of dependencies

**note**: The requirements.txt file has been updated and is now safe to use (as of this fork).

## Relevant files
To view a general API overview of the package, see the notebooks in the `demo` directory. These include demo's on predicting IV, Tg, and running the joint model. Examples of both cross validation and regular training are shown. 

To modify model architecture, please see the models in the `polymerlearn/models/gnn` directory. This contains models to perform IV, Tg, and joint prediction, including some experimental models with which the team has worked with.

## Questions?
If you have any questions, please reach out to Owen (owen_queen@hms.harvard.edu).

## Citation

If you want to cite our code or paper, please use the following BibTex entry:
```
@article{queen2023polymer, 
title={Polymer graph neural networks for multitask property learning}, 
volume={9}, 
ISSN={2057-3960}, 
DOI={10.1038/s41524-023-01034-3}, 
number={11}, 
journal={npj Computational Materials}, 
publisher={Nature Publishing Group}, 
author={Queen, Owen and McCarver, Gavin A. and Thatigotla, Saitheeraj and Abolins, Brendan P. and Brown, Cameron L. and Maroulas, Vasileios and Vogiatzis, Konstantinos D.}, 
year={2023}, 
pages={1–10}, 
language={en} 
}
```
