# GSOC Quantum Diffusion Model

This is a research project for ML4Sci with Google Summer of Code aimed at building a quantum denoising diffusion model.

## Description

The mid-term update blog for this project can be accessed here: [QDM Part I](https://medium.com/@mashapotatoes/gsoc-2024-quantum-diffusion-models-for-high-energy-physics-892e59ddcd3e).

The final blog can be accessed here: [QDM Part II](https://medium.com/@mashapotatoes/6e693d625931).

More details can be found at the [MLNCP NeurIPS 2024 Workshop](https://openreview.net/pdf?id=vUQLzDAdqt) website.

## Getting Started

### Dependencies and Installation

* ``` pip install requirements.txt ``` to download all dependencies in your own environment
* All code and model training can run locally on cropped data (16x16) and smaller sample sizes (e.g. 1k instead of 100k samples)
* Quantum or hybrid models use Pennylane for simulations, which can be much slower than the classical variant, so experimenting with the device could be helpful depending on hardware availability

### Executing program

* Most of the code is in Jupyter notebooks with preloaded examples
* The utils scripts are in .py files with helper functions and statistics
* Run each notebook separately cell by cell or export to python scripts


# Tutorial

推荐入门顺序

1. 先搞清“量子电路长什么样”
conceptualization/circuit_visualization.ipynb
画的是 64fully_quantum 里用的那类电路（AngleEmbedding + StronglyEntanglingLayers）。
不涉及训练，只跑几行就能看到电路图，适合建立直观。

2. 理解“数据怎么进、怎么出”
encoding_testing.ipynb
测的是：编码 → 解码、flip、统计与画图。
帮你弄清：原始数据 → 编码空间 → 再解码回去，这条管线在干什么，不涉及完整扩散训练。

3. 从“轻量混合”上手训练
hybrid_dm.ipynb
用 MNIST，编码是简单的 sin/cos（模仿量子特征图），扩散部分是经典的。
数据小、跑得快，容易看到“编码 → 扩散 → 解码”的完整流程，再去看 64fully_quantum 会轻松很多。

4. 再看“全量子”主实验
64fully_quantum.ipynb
编码、加噪（Haar）、去噪（PQC）都涉及量子，是你一直在问的那一套。
建议在前三个跑过、概念捋清后再完整跑一遍，并对照前面学到的“电路长什么样”“编码/解码怎么走”。


