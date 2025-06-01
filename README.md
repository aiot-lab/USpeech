<div align="center"> 

# USpeech: Ultrasound-Enhanced Speech with Minimal Human Effort via Cross-Modal Synthesis
</div>

<div align="center">   

[![Static Badge](https://img.shields.io/badge/arXiv-PDF-green?style=flat&logo=arXiv&logoColor=B31B1B)](https://arxiv.org/abs/2410.22076) [![YouTube Badge](https://img.shields.io/badge/Video-Watch-red?&logo=youtube&logoColor=FF0000)](https://aiot-lab.github.io/USpeech/src/videos/video.mp4) [![Project Page](https://img.shields.io/badge/Project%20Page-USpeech-yellow.svg?logo=github&logoColor=FFFFFF)](https://aiot-lab.github.io/USpeech/) [![App Download](https://img.shields.io/badge/App%20Download-OneDrive-purple.svg?logo=android&logoColor=3DDC84)](https://connecthkuhk-my.sharepoint.com/:u:/g/personal/lucayu_connect_hku_hk/EWxCZ_CusdtOrr4X6nGCsK4BAuccBTxwR4g1MDQNfpAjtA?e=Qy7AFe) [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

</div>

<div align="center">
    <a href=https://lucayu.me/>
        Luca Jiang-Tao Yu
    </a>
    ,
    <a href=https://zhaorunning.github.io/>
        Running Zhao
    </a>
    ,
    <a href=https://sijieji.github.io/>
        Sijie Ji
    </a>
    ,
    <a href=https://www.eee.hku.hk/~iotlab/EdithNgai.html>
        Edith C.H. Ngai
    </a>
    ,
    <a href=https://cswu.me/>
        Chenshu Wu
    </a>
</div>

<div align="center">

The University of Hong Kong
</div>
The official implementation of USpeech: Ultrasound-Enhanced Speech with Minimal Human Effort via Cross-Modal Synthesis, accepted by ACM Ubicomp/IMWUT 2025.

---

## Abstract
Speech enhancement is crucial for ubiquitous human-computer interaction. Recently, ultrasound-based acoustic sensing has emerged as an attractive choice for speech enhancement because of its superior ubiquity and performance. However, due to inevitable interference from unexpected and unintended sources during audio-ultrasound data acquisition, existing solutions rely heavily on human effort for data collection and processing. This leads to significant data scarcity that limits the full potential of ultrasound-based speech enhancement. To address this, we propose USpeech, a cross-modal ultrasound synthesis framework for speech enhancement with minimal human effort. At its core is a two-stage framework that establishes the correspondence between visual and ultrasonic modalities by leveraging audio as a bridge. This approach overcomes challenges from the lack of paired video-ultrasound datasets and the inherent heterogeneity between video and ultrasound data. Our framework incorporates contrastive video-audio pre-training to project modalities into a shared semantic space and employs an audio-ultrasound encoder-decoder for ultrasound synthesis. We then present a speech enhancement network that enhances speech in the time-frequency domain and recovers the clean speech waveform via a neural vocoder. Comprehensive experiments show USpeech achieves remarkable performance using synthetic ultrasound data comparable to physical data, outperforming state-of-the-art ultrasound-based speech enhancement baselines.

<p align="center"> <img src='src/figures/thumbnail.jpg' align="center"> </p>

---
## Setup Instructions
To get started with USpeech, follow these steps:
1. Clone the GitHub repository:
``` bash
$ git clone https://github.com/aiot-lab/USpeech.git
$ cd USpeech
$ pip install -r requirements.txt

# Install ParallelWaveGAN under the USpeech folder (https://github.com/kan-bayashi/ParallelWaveGAN)
$ git clone https://github.com/kan-bayashi/ParallelWaveGAN.git
$ cd ParallelWaveGAN
$ pip install -e .
```
2. Configure dataset paths, preprocessing parameters, and training settings in the ```config.yaml``` file.

3. Run the code in synthesis and enhancement models.

---

## Required Files
- Datasets
    - [LRW Dataset](https://www.robots.ox.ac.uk/~vgg/data/lip_reading/lrw1.html)
    - [LJSpeech Dataset](https://keithito.com/LJ-Speech-Dataset/)
    - [TIMIT Dataset](https://catalog.ldc.upenn.edu/LDC93S1)
    - [VCTK Dataset](https://datashare.ed.ac.uk/handle/10283/3443)
    - [Nonspeech7k Dataset](https://zenodo.org/records/6967442)

- Pretrained Models
    - [Slowonly Model](https://github.com/open-mmlab/mmaction2/tree/main/configs/recognition/slowonly)
    - [PANN Model](https://github.com/qiuqiangkong/audioset_tagging_cnn)

---

## Repository Structure
```
.
├── config.yaml
├── evaluation.py
├── preprocessing
│   ├── LRW_dataset_preprocessing.py
│   ├── collected_dataset_preprocessing.py
│   └── noisy_collected_dataset_preprocessing.py
├── synthesis.py
├── uspeech_enhancement_model
│   ├── __init__.py
│   ├── dataset.py
│   ├── loss.py
│   ├── model.py
│   ├── modules
│   │   ├── UNet.py
│   │   ├── UNet_parts.py
│   │   ├── __init__.py
│   │   └── bottleneck_transformer.py
│   └── train.py
└── uspeech_synthesis_model
    ├── __init__.py
    ├── modules
    │   ├── __init__.py
    │   ├── pann.py
    │   ├── slowonly.py
    │   ├── ultrasoundAudioModel.py
    │   ├── ultrasoundDecoder.py
    │   └── videoAudioModel.py
    ├── pretrain.py
    ├── pretrain_dataset.py
    ├── pretrain_loss.py
    ├── scheduler.py
    ├── train.py
    ├── train_dataset.py
    └── train_loss.py
```

---

## Citation
```
@article{yu2024uspeech,
  title={USpeech: Ultrasound-Enhanced Speech with Minimal Human Effort via Cross-Modal Synthesis},
  author={Yu, Luca Jiang-Tao and Zhao, Running and Ji, Sijie and Ngai, Edith CH and Wu, Chenshu},
  journal={arXiv preprint arXiv:2410.22076},
  year={2024}
}
```

## License
This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.
