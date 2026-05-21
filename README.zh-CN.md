# Marigold 计算机视觉

本项目实现了 Marigold，这是一种用于估计图像特性的计算机视觉方法。我们最初在 CVPR 2024 论文 **"Repurposing Diffusion-Based Image Generators for Monocular Depth Estimation"** 中提出它，用于提取高分辨率深度图；随后又在后续论文 **"Marigold: Affordable Adaptation of Diffusion-Based Image Generators for Image Analysis"** 中，将该方法扩展到其他模态。

## Marigold：以低成本方式将基于扩散的图像生成器适配到图像分析

[![Website](doc/badges/badge-website.svg)](https://marigoldcomputervision.github.io)
[![Paper](doc/badges/badge-pdf.svg)](https://arxiv.org/abs/2505.09358)
[![Depth Demo](https://img.shields.io/badge/🤗%20Depth-Demo-yellow)](https://huggingface.co/spaces/prs-eth/marigold)
[![Normals Demo](https://img.shields.io/badge/🤗%20Normals-Demo-yellow)](https://huggingface.co/spaces/prs-eth/marigold-normals)
[![Intrinsics Demo](https://img.shields.io/badge/🤗%20Image%20Intrinsics-Demo-yellow)](https://huggingface.co/spaces/prs-eth/marigold-iid)
[![Depth Model](https://img.shields.io/badge/🤗%20Depth-Model-green)](https://huggingface.co/prs-eth/marigold-depth-v1-1)
[![Normals Model](https://img.shields.io/badge/🤗%20Normals-Model-green)](https://huggingface.co/prs-eth/marigold-normals-v1-1)
[![Intrinsics Appearance Model](https://img.shields.io/badge/🤗%20Image%20Intrinsics%20Appearance-Model-green)](https://huggingface.co/prs-eth/marigold-iid-appearance-v1-1)
[![Intrinsics Lighting Model](https://img.shields.io/badge/🤗%20Image%20Intrinsics%20Lighting-Model-green)](https://huggingface.co/prs-eth/marigold-iid-lighting-v1-1)
[![Diffusers Tutorial](doc/badges/badge-hfdiffusers.svg)](https://huggingface.co/docs/diffusers/using-diffusers/marigold_usage)

团队：
[Bingxin Ke](http://www.kebingxin.com/)、
[Kevin Qu](https://www.linkedin.com/in/kevin-qu-b3417621b/)、
[Tianfu Wang](https://tianfwang.github.io/)
[Nando Metzger](https://nandometzger.github.io/)、
[Shengyu Huang](https://shengyuh.github.io/)、
[Bo Li](https://www.linkedin.com/in/bobboli0202/)、
[Anton Obukhov](https://www.obukhov.ai/)、
[Konrad Schindler](https://scholar.google.com/citations?user=FZuNgqIAAAAJ)

我们提出了 Marigold，一系列条件生成模型以及一套微调协议，用于从 Stable Diffusion 等预训练 latent diffusion model 中提取知识，并将其适配到密集图像分析任务，包括单目深度估计、表面法线预测和 intrinsic decomposition。Marigold 对预训练 latent diffusion model 架构只需要最小修改，能够在单张 GPU 上使用小规模合成数据训练数天，并展示出最先进的 zero-shot 泛化能力。

![teaser_all](doc/teaser_marigold_all.jpg)

## 将基于扩散的图像生成器重新用于单目深度估计

[![Website](doc/badges/badge-website.svg)](https://marigoldmonodepth.github.io)
[![Paper](doc/badges/badge-pdf.svg)](https://arxiv.org/abs/2312.02145)
[![Hugging Face Space](https://img.shields.io/badge/🤗%20Hugging%20Face-Space-yellow)](https://huggingface.co/spaces/prs-eth/marigold)
[![Hugging Face Model](https://img.shields.io/badge/🤗%20Hugging%20Face%20-Model-green)](https://huggingface.co/prs-eth/marigold-depth-v1-1)
[![Open In Colab](doc/badges/badge-colab.svg)](https://colab.research.google.com/drive/12G8reD13DdpMie5ZQlaFNo2WCGeNUH-u?usp=sharing)

发表于 **CVPR 2024（Oral，Best Paper Award Candidate）**<br>
团队：
[Bingxin Ke](http://www.kebingxin.com/)、
[Anton Obukhov](https://www.obukhov.ai/)、
[Shengyu Huang](https://shengyuh.github.io/)、
[Nando Metzger](https://nandometzger.github.io/)、
[Rodrigo Caye Daudt](https://rcdaudt.github.io/)、
[Konrad Schindler](https://scholar.google.com/citations?user=FZuNgqIAAAAJ)

我们提出了 Marigold，一个用于单目深度估计的扩散模型及其配套微调协议。它的核心原则是利用现代生成式图像模型中存储的丰富视觉知识。我们的模型源自 Stable Diffusion，并使用合成数据进行微调，能够 zero-shot 迁移到未见过的数据，在单目深度估计上取得最先进的结果。

![teaser_depth](doc/teaser_marigold_depth.png)

## 📢 新闻
2025-05-15：发布 Marigold Intrinsic Image Decomposition 的代码和一个 [checkpoint](https://huggingface.co/prs-eth/marigold-iid-lighting-v1-1)，可预测 Albedo、diffuse Shading 和 non-diffuse Residual（Marigold-IID-Lighting v1.1）。<br>
2025-05-15：发布 Marigold Intrinsic Image Decomposition 的代码和一个 [checkpoint](https://huggingface.co/prs-eth/marigold-iid-appearance-v1-1)，可预测 Albedo、Roughness 和 Metallicity（Marigold-IID-Appearance v1.1）。<br>
2025-05-15：发布 Marigold Surface Normals Estimation（v1.1）的代码和一个 [checkpoint](https://huggingface.co/prs-eth/marigold-normals-v1-1)。<br>
2025-05-15：发布更新后的 Marigold Depth（v1.1）[checkpoint](https://huggingface.co/prs-eth/marigold-depth-v1-1)，该模型使用了更新后的 noise scheduler 设置（zero-SNR 和 trailing timestamps）以及数据增强。<br>
2024-05-28：训练代码已发布。<br>
2024-05-27：Marigold pipelines 从 v0.28.0 [release](https://github.com/huggingface/diffusers/releases/tag/v0.28.0) 开始被合并进 `diffusers` 核心！<br>
2024-03-23：添加 Latent Consistency Model（LCM）[checkpoint](https://huggingface.co/prs-eth/marigold-depth-lcm-v1-0)。<br>
2024-03-04：论文被 CVPR 2024 接收。<br>
2023-12-22：贡献到 Diffusers [community pipeline](https://github.com/huggingface/diffusers/tree/main/examples/community#marigold-depth-estimation)。<br>
2023-12-19：将 [license](LICENSE.txt) 更新为 Apache License, Version 2.0。<br>
2023-12-08：添加第一个用于深度估计的交互式 [Hugging Face Space Demo](https://huggingface.co/spaces/prs-eth/marigold)。<br>
2023-12-05：添加 [Google Colab](https://colab.research.google.com/drive/12G8reD13DdpMie5ZQlaFNo2WCGeNUH-u?usp=sharing)。<br>
2023-12-04：添加 [arXiv paper](https://arxiv.org/abs/2312.02145) 和推理代码（即本仓库）。

## 🚀 使用方式

**我们提供了几种与 Marigold 交互的方式**：

1. 一组免费的在线交互式 demo：
<a href="https://huggingface.co/spaces/prs-eth/marigold"><img src="https://img.shields.io/badge/🤗%20Depth-Demo-yellow" height="16"></a>
<a href="https://huggingface.co/spaces/prs-eth/marigold-normals"><img src="https://img.shields.io/badge/🤗%20Normals-Demo-yellow" height="16"></a>
<a href="https://huggingface.co/spaces/prs-eth/marigold-iid"><img src="https://img.shields.io/badge/🤗%20Image%20Intrinsics-Demo-yellow" height="16"></a>
（感谢 HF 团队提供 GPU grants）

1. Marigold pipelines 是
<a href="https://huggingface.co/docs/diffusers/using-diffusers/marigold_usage"><img src="doc/badges/badge-hfdiffusers.svg" height="16"></a> 的一部分，这是一个 diffusion 🧨 的一站式平台！

1. 在本地运行 demo（需要 GPU 和 `nvidia-docker2`，见 [Installation Guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)）：
`docker run -it -p 7860:7860 --platform=linux/amd64 --gpus all registry.hf.space/prs-eth-marigold:latest python app.py`

1. Google Colab 上的扩展 demo：<a href="https://colab.research.google.com/drive/12G8reD13DdpMie5ZQlaFNo2WCGeNUH-u?usp=sharing"><img src="doc/badges/badge-colab.svg" height="16"></a>

1. 如果你只是想查看示例，请访问我们的 gallery：<a href="https://marigoldcomputervision.github.io"><img src="doc/badges/badge-website.svg" height="16"></a>

1. 最后，基于此代码库进行本地开发的说明见下文。

## 🛠️ 设置

推理代码已在以下环境中测试：

- Ubuntu 22.04 LTS、Python 3.10.12、CUDA 11.7、GeForce RTX 3090（pip）

### 🪧 Windows 用户注意事项

我们建议在 WSL2 中运行代码：

1. 按照 [installation guide](https://learn.microsoft.com/en-us/windows/wsl/install#install-wsl-command) 安装 WSL。
1. 按照 [installation guide](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#cuda-support-for-wsl-2) 为 WSL 安装 CUDA 支持。
1. 你的磁盘可以在 `/mnt/<drive letter>/` 下找到；更多细节请查看 [WSL FAQ](https://learn.microsoft.com/en-us/windows/wsl/faq#how-do-i-access-my-c--drive-)。然后进入你选择的工作目录。

### 📦 仓库

克隆仓库（需要 git）：

```bash
git clone https://github.com/prs-eth/Marigold.git
cd Marigold
```

### 💻 依赖

安装依赖：

```bash
python -m venv venv/marigold
source venv/marigold/bin/activate
pip install -r requirements.txt
```

运行推理脚本前，请保持环境处于激活状态。
重启终端会话后，需要再次激活该环境。

## 🏃 在你自己的图像上测试

### 📷 准备图像

使用我们论文中选取的图像：

```bash
bash script/download_sample_data.sh
```

或者把你自己的图像放入一个目录，例如 `input/in-the-wild_example`，然后运行下面的推理命令。

### 🚀 运行推理（用于实际使用）

```bash
# Depth
python script/depth/run.py \
    --checkpoint prs-eth/marigold-depth-v1-1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example \
    --fp16
```

```bash
# Normals
python script/normals/run.py \
    --checkpoint prs-eth/marigold-normals-v1-1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example \
    --fp16
```

```bash
# IID (appearance model)
python script/iid/run.py \
    --checkpoint prs-eth/marigold-iid-appearance-v1-1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example \
    --fp16

# IID (lighting model)
python script/iid/run.py \
    --checkpoint prs-eth/marigold-iid-lighting-v1-1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example \
    --fp16
```

### ⚙️ 推理设置

默认设置已经针对最佳结果进行了优化。不过，也可以自定义代码行为：

- `--half_precision` 或 `--fp16`：使用半精度（16-bit float）运行，以获得更快速度并减少显存使用，但可能导致次优结果。

- `--ensemble_size`：ensemble 中的推理次数。更大的值在评测中通常会得到更好结果，但推理更慢；大多数情况下 1 就足够。默认值：1。

- `--denoise_steps`：去噪扩散步骤数。默认设置定义在模型 checkpoint 中，对大多数情况已经足够。

- 默认情况下，推理脚本会把输入图像 resize 到 *processing resolution*，然后再把预测结果 resize 回原始分辨率。这样质量最好，因为 Marigold 源自 Stable Diffusion，而 Stable Diffusion 在 768x768 分辨率上效果最好。

  - `--processing_res`：处理分辨率；设为 0 表示直接使用输入分辨率进行处理。未指定时（`None`），会从模型配置读取默认设置。默认值：`None`。
  - `--output_processing_res`：输出处理分辨率下的结果，而不是将其上采样回输入分辨率。默认值：False。
  - `--resample_method`：用于 resize 图像和深度预测的重采样方法。可选 `bilinear`、`bicubic` 或 `nearest`。默认值：`bilinear`。

- `--seed`：可以设置随机种子以提高额外的可复现性。默认值：None（不设种子）。注意：强制设置 `--batch_size 1` 有助于提高可复现性。若要保证完全可复现，需要使用 [deterministic mode](https://pytorch.org/docs/stable/notes/randomness.html#avoiding-nondeterministic-algorithms)。
- `--batch_size`：重复推理的 batch size。默认值：0（自动确定最佳值）。
- `--color_map`：用于给深度预测上色的 [Colormap](https://matplotlib.org/stable/users/explain/colors/colormaps.html)。默认值：Spectral。设为 `None` 可跳过彩色深度图生成。
- `--apple_silicon`：使用 Apple Silicon MPS 加速。


### 🎮 运行推理（用于学术比较）

这些设置对应我们的论文。用于学术比较时，请使用以下设置运行（如果你只是想在自己的图像上快速推理，可以把 `--ensemble_size` 设为 1）。

```bash
# Depth
python script/depth/run.py \
    --checkpoint prs-eth/marigold-depth-v1-1 \
    --denoise_steps 1 \
    --ensemble_size 10 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

```bash
# Normals
python script/normals/run.py \
    --checkpoint prs-eth/marigold-normals-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 10 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

```bash
# IID (appearance model)
python script/iid/run.py \
    --checkpoint prs-eth/marigold-iid-appearance-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example

# IID (lighting model)
python script/iid/run.py \
    --checkpoint prs-eth/marigold-iid-lighting-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

```bash
# Depth（原始 CVPR 版本）
python script/depth/run.py \
    --checkpoint prs-eth/marigold-depth-v1-0 \
    --denoise_steps 50 \
    --ensemble_size 10 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

你可以在 `output` 目录中找到所有结果。祝你玩得开心！


### ⬇ Checkpoint 缓存

默认情况下，checkpoint（[depth](https://huggingface.co/prs-eth/marigold-depth-v1-1)、[normals](https://huggingface.co/prs-eth/marigold-normals-v1-1)、[iid](https://huggingface.co/prs-eth/marigold-iid-appearance-v1-1)）会被存储在 Hugging Face cache 中。
`HF_HOME` 环境变量定义它的位置，并且可以被覆盖，例如：

```bash
export HF_HOME=$(pwd)/cache
```

或者使用下面的脚本在本地下载 checkpoint weights：

```bash
bash script/download_weights.sh marigold-depth-v1-1           # depth checkpoint
bash script/download_weights.sh marigold-normals-v1-1         # normals checkpoint
bash script/download_weights.sh marigold-iid-appearance-v1-1  # iid appearance checkpoint
bash script/download_weights.sh marigold-iid-lighting-v1-1    # iid lighting checkpoint
# bash script/download_weights.sh marigold-depth-v1-0         # CVPR depth checkpoint
```

推理时，指定 checkpoint 路径：

```bash
# Depth
python script/depth/run.py \
    --checkpoint checkpoint/marigold-depth-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

```bash
# Normals
python script/normals/run.py \
    --checkpoint checkpoint/marigold-normals-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

```bash
# IID (appearance model)
python script/iid/run.py \
    --checkpoint checkpoint/marigold-iid-appearance-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example

# IID (lighting model)
python script/iid/run.py \
    --checkpoint checkpoint/marigold-iid-lighting-v1-1 \
    --denoise_steps 4 \
    --ensemble_size 1 \
    --input_rgb_dir input/in-the-wild_example \
    --output_dir output/in-the-wild_example
```

## 🦿 在测试数据集上评估 <a name="evaluation"></a>
安装额外依赖：

```bash
pip install -r requirements+.txt -r requirements.txt
```

设置数据目录变量（评估脚本中也需要它），并将评估数据集（[depth](https://share.phys.ethz.ch/~pf/bingkedata/marigold/evaluation_dataset)、[normals](https://share.phys.ethz.ch/~pf/bingkedata/marigold/marigold_normals/evaluation_dataset)）下载到对应子文件夹：

```bash
export BASE_DATA_DIR=<YOUR_DATA_DIR>  # Set target data directory

# Depth
wget -r -np -nH --cut-dirs=4 -R "index.html*" -P ${BASE_DATA_DIR} https://share.phys.ethz.ch/~pf/bingkedata/marigold/evaluation_dataset/

# Normals
wget -r -np -nH --cut-dirs=4 -R "index.html*" -P ${BASE_DATA_DIR} https://share.phys.ethz.ch/~pf/bingkedata/marigold/marigold_normals/evaluation_dataset.zip
unzip ${BASE_DATA_DIR}/evaluation_dataset.zip -d ${BASE_DATA_DIR}/
rm -f ${BASE_DATA_DIR}/evaluation_dataset.zip
```
关于 intrinsic image decomposition 测试数据的下载说明，请参考 [iid-appearance instructions](script/iid/dataset_preprocess/interiorverse_appearance/README.md) 和 [iid-lighting instructions](script/iid/dataset_preprocess/hypersim_lighting/README.md)。

运行推理和评估脚本，例如：

```bash
# Depth
bash script/depth/eval/11_infer_nyu.sh  # Run inference
bash script/depth/eval/12_eval_nyu.sh   # Evaluate predictions
```

```bash
# Normals
bash script/normals/eval/11_infer_scannet.sh  # Run inference
bash script/normals/eval/12_eval_scannet.sh   # Evaluate predictions
```

```bash
# IID
bash script/iid/eval/11_infer_appearance_interiorverse.sh  # Run inference
bash script/iid/eval/12_eval_appearance_interiorverse.sh   # Evaluate predictions

bash script/iid/eval/21_infer_lighting_hypersim.sh  # Run inference
bash script/iid/eval/22_eval_lighting_hypersim.sh   # Evaluate predictions
```

```bash
# Depth（原始 CVPR 版本）
bash script/depth/eval_old/11_infer_nyu.sh  # Run inference
bash script/depth/eval_old/12_eval_nyu.sh   # Evaluate predictions
```

注意：虽然已经设置了 seed，但不同硬件上的结果仍可能略有不同。

## 🏋️ 训练

基于先前创建的环境，安装扩展 requirements：

```bash
pip install -r requirements++.txt -r requirements+.txt -r requirements.txt
```

为数据目录设置环境参数：

```bash
export BASE_DATA_DIR=YOUR_DATA_DIR        # directory of training data
export BASE_CKPT_DIR=YOUR_CHECKPOINT_DIR  # directory of pretrained checkpoint
```

将 Stable Diffusion v2 [checkpoint](https://huggingface.co/stabilityai/stable-diffusion-2) 下载到 `${BASE_CKPT_DIR}`（[backup link](https://share.phys.ethz.ch/~pf/bingkedata/marigold/checkpoint/stable-diffusion-2.tar)）。

### 准备训练数据
**Depth**

准备 [Hypersim](https://github.com/apple/ml-hypersim) 和 [Virtual KITTI 2](https://europe.naverlabs.com/research/computer-vision/proxy-virtual-worlds-vkitti-2/) 数据集，并保存到 `${BASE_DATA_DIR}`。关于 Hypersim 预处理，请参考 [this README](script/depth/dataset_preprocess/hypersim/README.md)。

**Normals**

准备 [Hypersim](https://github.com/apple/ml-hypersim)、[Interiorverse](https://interiorverse.github.io/) 和 [Sintel](http://sintel.is.tue.mpg.de/) 数据集，并保存到 `${BASE_DATA_DIR}`。关于 Hypersim 预处理，请参考 [this README](script/normals/dataset_preprocess/hypersim/README.md)；关于 Interiorverse，请参考 [this README](script/normals/dataset_preprocess/interiorverse/README.md)；关于 Sintel，请参考 [this README](script/normals/dataset_preprocess/sintel/README.md)。

**Intrinsic Image Decomposition**

*Appearance model*：准备 [Interiorverse](https://interiorverse.github.io/) 数据集，并保存到 `${BASE_DATA_DIR}`。关于 Interiorverse 预处理，请参考 [this README](script/iid/dataset_preprocess/interiorverse_appearance/README.md)。

*Lighting model*：准备 [Hypersim](https://github.com/apple/ml-hypersim) 数据集，并保存到 `${BASE_DATA_DIR}`。关于 Hypersim 预处理，请参考 [this README](script/iid/dataset_preprocess/hypersim_lighting/README.md)。


### 运行训练脚本

```bash
# Depth
python script/depth/train.py --config config/train_marigold_depth.yaml
```

```bash
# Normals
python script/normals/train.py --config config/train_marigold_normals.yaml
```

```bash
# IID (appearance model)
python script/iid/train.py --config config/train_marigold_iid_appearance.yaml

# IID (lighting model)
python script/iid/train.py --config config/train_marigold_iid_lighting.yaml
```

从 checkpoint 恢复，例如：

```bash
# Depth
python script/depth/train.py --resume_run output/marigold_base/checkpoint/latest
```

```bash
# Normals
python script/normals/train.py --resume_run output/train_marigold_normals/checkpoint/latest
```

```bash
# IID (appearance model)
python script/iid/train.py --resume_run output/train_marigold_iid_appearance/checkpoint/latest

# IID (lighting model)
python script/iid/train.py --resume_run output/train_marigold_iid_lighting/checkpoint/latest
```

### 组合 checkpoint：
训练期间只有 U-Net 和 scheduler config 会被更新。它们保存在训练目录中。若要使用训练结果运行推理 pipeline：
- 用 `checkpoint` 输出文件夹中的 `unet` 文件夹，替换 Marigold checkpoints 中的 `unet` 文件夹。
- 用训练期间生成的 `checkpoint/scheduler_config.json` 替换 Marigold checkpoints 中的 `scheduler/scheduler_config.json` 文件。
然后参考 [this section](#evaluation) 进行评估。

**注意**：虽然已经设置了随机种子，但训练结果在不同硬件上可能略有不同。建议训练过程中不要中断。

## ✏️ 贡献

请参考 [this](CONTRIBUTING.md) 说明。

## 🤔 故障排查

| 问题 | 解决方案 |
|----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| (Windows) WSL 上 bash 脚本的 DOS 格式无效 | 运行 `dos2unix <script_name>` 转换脚本格式 |
| (Windows) WSL 报错：`Could not load library libcudnn_cnn_infer.so.8. Error: libcuda.so: cannot open shared object file: No such file or directory` | 运行 `export LD_LIBRARY_PATH=/usr/lib/wsl/lib:$LD_LIBRARY_PATH` |
| 训练需要很长时间才能开始 | 使用文件夹形式的数据，而不是 tar 文件（需要修改配置文件）。 |



## 🎓 引用

请引用我们的论文：

```bibtex
@InProceedings{ke2023repurposing,
  title={Repurposing Diffusion-Based Image Generators for Monocular Depth Estimation},
  author={Bingxin Ke and Anton Obukhov and Shengyu Huang and Nando Metzger and Rodrigo Caye Daudt and Konrad Schindler},
  booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2024}
}

@misc{ke2025marigold,
  title={Marigold: Affordable Adaptation of Diffusion-Based Image Generators for Image Analysis},
  author={Bingxin Ke and Kevin Qu and Tianfu Wang and Nando Metzger and Shengyu Huang and Bo Li and Anton Obukhov and Konrad Schindler},
  year={2025},
  eprint={2505.09358},
  archivePrefix={arXiv},
  primaryClass={cs.CV}
}
```

## 🎫 许可证

本工作的代码使用 Apache License, Version 2.0 授权（定义见 [LICENSE](LICENSE.txt)）。

模型使用 RAIL++-M License 授权（定义见 [LICENSE-MODEL](LICENSE-MODEL.txt)）。

下载并使用代码和模型即表示你分别同意 [LICENSE](LICENSE.txt) 和 [LICENSE-MODEL](LICENSE-MODEL.txt) 中的条款。
