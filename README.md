# Corrformer (Nature Machine Intelligence)

In this [paper](https://www.nature.com/articles/s42256-023-00667-9), we present Corrformer with the Multi-Correlation mechanism, which can unify the temporal auto-correlation and spatial correlation in a learned multiscale tree structure.

- Corrformer reduces the canonical double quadratic complexity of spatiotemporal modeling to linear in spatial modeling and log-linear in temporal modeling, **firstly achieving collaborative forecasts for tens of thousands of stations within a unified deep model**.
- Corrformer can generate interpretable predictions based on inferred propagation directions of weather processes, **facilitating a fully data-driven AI paradigm for discovering insights for meteorological science**.
- Corrformer yields **state-of-the-art forecasts on global, regional and citywide datasets** with high confidence, beating classical statistical methods, latest deep models, and comparing favorably to numerical methods in near-surface forecasting.

:triangular_flag_on_post:**News** (2023.06) Our paper has been published in Nature Machine Intelligence as the [Cover Article](https://www.nature.com/natmachintell/volumes/5/issues/6).


## Code Structure

```python
|-- Corrformer
   |-- data_provider # Data loader
   |-- exp # Pipelines for train, validation and test
   |-- layers 
   |   |-- Embed.py # Equ (1) of the paper
   |   |-- Corrformer_EncDec.py # Equ (2) and Equ (3) of the paper
   |   |-- Causal_Conv.py # Causal conv for Cross-Correlation
   |   |-- Multi_Correlation.py # Equ (5)-(10) of the paper
   |-- models
   |   |-- Corrformer.py # Overall framework
   |-- utils
   |-- scripts # Running scripts
   |-- dataset # Place the download datsets here
   |-- checkpoints # Place the output or pretrained models here
```

## Reproduction

1. Find a device with GPU support. Our experiment is conducted on a single RTX 24GB GPU and in the Linux system.
2. Install Python 3.6, PyTorch 1.7.1. The following script can be convenient.

```bash
pip install -r requirements.txt # take about 5 minutes
```

2. Download the dataset from [[Tsinghua Cloud]](https://cloud.tsinghua.edu.cn/d/f5b13a194255457c9460/). And place them under the `./dataset` folder.

3. Train and evaluate the model with the following scripts.

```shell
bash ./scripts/Global_Temp/Corrformer.sh # take about 18 hours
bash ./scripts/Global_Wind/Corrformer.sh # take about 18 hours
```

Note: Since the raw data for Global Temp and Global Wind from the NCEI has been multiplied by ten times, the actual MSE and MAE for these two benchmarks should be divided by 100 and 10 respectively.

## Demo

For a simple demo, we would recommend the experiments with the pre-trained models, which can provide a fast test of our code. Here are the detailed instructions:

1. Configure the environment with the above instructions. Note that the following experiments will take 4GB GPU memory.
2. Download the datasets and pretrained models from [[Datasets]](https://cloud.tsinghua.edu.cn/d/f5b13a194255457c9460/) and [[Pretrained Models]](https://cloud.tsinghua.edu.cn/d/5986f3be94ff4f1c97e5/). Place the pretrained models under the `./checkpoints` folder.
3. Execute the demo with the following scripts.

```bash
bash ./scripts/Demo/Global_Temp_demo.sh # take about 35 minutes
bash ./scripts/Demo/Global_Wind_demo.sh # take about 35 minutes
```

Note again: Since the raw data for Global Temp and Global Wind from the NCEI has been multiplied by ten times, **the actual MSE and MAE for these two benchmarks should be divided by 100 and 10 respectively**.

## Citation

If you find this repo useful, please cite our paper.

```
@article{wu2023corrformer,
  title={Interpretable Weather Forecasting for Worldwide Stations with a Unified Deep Model},
  author={Haixu Wu and Hang Zhou and Mingsheng Long and Jianmin Wang},
  journal={Nature Machine Intelligence},
  year={2023},
}
```

## Contact
If you have any questions or suggestions, feel free to contact Haixu Wu (whx20@mails.tsinghua.edu.cn).

