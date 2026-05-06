<h1 align="center">
Boundary-Aware Uncertainty Quantification
    
for Wildfire Spread Prediction

</h1>
<p align="center">
  <sub>
    <a href="https://www.linkedin.com/in/jonas-vilho-funk-b66636158">Jonas V. Funk</a>
  </sub>
</p>


<div align="center">
    
[![arXiv](https://img.shields.io/badge/arXiv-2605.03148-b31b1b.svg)](https://arxiv.org/abs/2605.03148)

</div>

---

# Abstract
Shifting the focus of uncertainty quantification (UQ) for wildfire spread prediction toward a more operationally relevant approach. The **Fire-Centered Evaluation Region (FCER)** framework is a spatially conditioned evaluation protocol to characterize UQ within critical fire zones. Use FCER to compare your models, exemplified here by comparing a Deep Ensemble against a distilled single-pass [DUDES](https://github.com/StevenLandgraf/DUDES) student model on the [WildfireSpreadTS](https://github.com/SebastianGer/WildfireSpreadTS) dataset.

<p align="center">
  <img src="https://github.com/user-attachments/assets/fbfacb06-f424-4789-9132-24f37006cd79"
       alt="Figure 2" />
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/2d582648-5c8e-4a61-9d28-a966bdd426f3"
       alt="Figure 1" />
</p>

---

# Repository Structure

```
WildfireUQ_Final/
│
├── third_party/                  # adapted from github.com/slahrichi/WildfireSpreadTS
│   ├── dataloader/               
│   │   ├── FireSpreadDataModule.py
│   │   ├── FireSpreadDataset.py
│   │   └── utils.py
│   └── models/
│       ├── BaseModel.py         
│       ├── SMPModel.py           
│       ├── SMPTempModel.py       
│       └── utae_paps_models/     
│
├── WildfireSpreadTS_HDF5/        # <<<< place here dataset HDF5 files
│
├── notebooks/
│   ├── 01_train_dudes.ipynb      
│   └── 02_fcer_evaluation.ipynb         
│
├── pretrained_weights/           # <<<< place here backbone .pth files
│  
└── results/                                      
```

# Setup
This setup was tested on Windows, runs on CPU only, and requires Python 3.11.

```bash
git clone https://github.com/jonasvilhofunk/WildfireUQ-FCER
cd WildfireUQ-FCER

# create virtual environment
py -3.11 -m venv .venv

# activate it in PowerShell
.venv\Scripts\Activate.ps1

# install dependencies
python -m pip install --upgrade pip
pip install -r requirements.txt

# optional: make this environment available as a Jupyter kernel
pip install ipykernel
python -m ipykernel install --user --name wildfireuq-fcer --display-name "Python FCER (.venv)"
```

## Prerequisites

This repository requires two external resources:

1. Download the [WildfireSpreadTS](https://github.com/SebastianGer/WildfireSpreadTS) dataset, convert them to **HDF5 format** (as done by the
preprocessing scripts in the WildfireSpreadTS repository)

    Link >>>> [https://zenodo.org/records/8006177](https://zenodo.org/records/8006177)

```
WildfireSpreadTS_HDF5/
├── 2018/
├── 2019/
├── 2020/
└── 2021/
```


2. Download checkpoints from [slahrichi](https://github.com/slahrichi/WildfireSpreadTS) for the Ensemble.

    Link >>>> [https://huggingface.co/saadlahrichi/WSTSPlus/tree/main/trained_model_weights](https://huggingface.co/saadlahrichi/WSTSPlus/tree/main/trained_model_weights)

```
pretrained_weights/
├── Res18UTAE_T5/Veg/ 
├── Res18Unet_T5/Veg/
└── Res18Unet_T1/Veg/
```


## Reproducing Results

Run the notebooks **in order**:

`01_train_dudes.ipynb` 

`02_fcer_evaluation.ipynb`


## Citation

If you use this code, please cite:

```bibtex
@misc{funk2026fcer,
      title={Boundary-Aware Uncertainty Quantification for Wildfire Spread Prediction}, 
      author={Jonas V. Funk},
      year={2026},
      eprint={2605.03148},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2605.03148}, 
}

```

## Acknowledgement
This repo is built upon:

```bibtex
@inproceedings{lahrichi2026improved,
  title={Improved wildfire spread prediction with time-series data and the WSTS+ benchmark},
  author={Lahrichi, Saad and Bova, Jake and Johnson, Jesse and Malof, Jordan},
  booktitle={Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision},
  pages={2890--2900},
  year={2026}
}
```

and

```bibtex
@inproceedings{
    gerard2023wildfirespreadts,
    title={WildfireSpread{TS}: A dataset of multi-modal time series for wildfire spread prediction},
    author={Sebastian Gerard and Yu Zhao and Josephine Sullivan},
    booktitle={Thirty-seventh Conference on Neural Information Processing Systems Datasets and Benchmarks Track},
    year={2023},
}
```