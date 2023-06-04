# creative-musician

## 1. Overview

在課堂上我們看到了Generative AI 創作文字、影像等，這讓我們好奇可不可以應用在音樂上面。究竟Generative AI可不可以做出與某個作曲家類似的作品？音樂的風格可以被找出規律嗎？多個音樂家的風格可以利用Generative AI被良好的融合嗎？

作為產生音樂的模型，使用者肯定是創作者偏多，並且他們使用的檔案格式以MIDI檔案占大多數。因此我們希望可以做出一個可以產生MIDI檔案的模型，並帶給使用者創作的靈感。

## 2. Prerequisite

將 repo clone 下來，由於我們使用了 submodule，因此 clone 時要注意加上 `--recursive` 選項：

```bash
git clone --recursive https://github.com/LittleD3092/creative-musician.git
```

更改 work directory 到 `bachsformer`：

```bash
cd creative-musician/bachsformer
```

從提供的 `yml` 檔案新增一個 conda 環境：

```bash
conda env create -f bachsformer.yml
```

- 注意這個檔案提供的版本可能不能在所有的電腦上執行。我們只有在 MacOS Ventura 13.0 上成功執行過。


## 3. Usage

### 3.1. 生成MIDI

你可以利用 `generate.py` 來產生一個 MIDI 檔案：

```bash
python generate.py
```

### 3.2. 訓練模型

在訓練模型前，你需要先將 MIDI 檔案放進 `creative-musician/bachsformer/data/midi` 資料夾中。

你可以利用 `train_vq_vae.py` 來訓練 VQ-VAE 模型：

```bash
python train_vq_vae.py
```

在訓練 VQ-VAE 模型之後，你可以利用 `train_transformer.py` 來訓練 Transformer 模型：

```bash
python train_transformer.py
```

## 4. Hyperparameters

- epochs: 10
- num_hiddens: 128
- num_residual_layers: 2
- num_residual_hiddens: 32
- num_embeddings: 16
- embedding_dim: 128
- commitment_cost: 0.25
- decay: 0.99

## 5. Experiment Results

`creative-musician/bachsformer/data/generated` 資料夾中提供了我們訓練出來的模型生成的 MIDI 檔案。

## 6. Reference

### 6.1. Related Papers:

[1] Dhariwal, Prafulla, et al. "Jukebox: A generative model for music." arXiv preprint arXiv:2005.00341 (2020), https://arxiv.org/abs/2005.00341.

[2] Han, Sangjun, Hyeongrae Ihm, and Woohyung Lim. "Symbolic Music Loop Generation with VQ-VAE." arXiv preprint arXiv:2111.07657 (2021), https://arxiv.org/abs/2111.07657.

[3] Neves, Pedro, Jose Fornari, and João Florindo. "Generating music with sentiment using Transformer-GANs." arXiv preprint arXiv:2212.11134 (2022), https://arxiv.org/abs/2212.11134.

[4] Van Den Oord, Aaron, and Oriol Vinyals. "Neural discrete representation learning." Advances in neural information processing systems 30 (2017), https://arxiv.org/abs/1711.00937v2.

### 6.2. Introduction Networks:

[5] “【機器學習2021】Transformer (上).” YouTube, 26 March 2021, https://www.youtube.com/watch?v=n9TlOhRjYoc.

[6] “【機器學習2021】Transformer (下).” YouTube, 9 April 2021, https://www.youtube.com/watch?v=N6aRv06iv2g. 

[7] “【DL】第 7 章 ：用于音乐生成的Transformers和 MuseGAN_music transformer_Sonhhxg_柒的博客.” CSDN博客, 8 March 2023, https://blog.csdn.net/sikh_0529/article/details/129371849#t12. 

[8] “一起幫忙解決難題，拯救 IT 人的一天.” iT 邦幫忙::一起幫忙解決難題，拯救IT 人的一天, https://ithelp.ithome.com.tw/articles/10206869. 

[9] “一起幫忙解決難題，拯救 IT 人的一天.” iT 邦幫忙::一起幫忙解決難題，拯救IT 人的一天, https://ithelp.ithome.com.tw/articles/10304388. 

[10] “论文阅读- Jukebox: A Generative Model for Music_jukebox: a generative model for music prafulla_七元权的博客.” CSDN博客, 30 April 2021, https://blog.csdn.net/zjuPeco/article/details/116159855. 

[11] “十分钟理解Transformer - 知乎.” 知乎专栏, https://zhuanlan.zhihu.com/p/82312421. 

[12] “论文解读| Transformer 原理深入浅出- 知乎.” 知乎专栏, https://zhuanlan.zhihu.com/p/110219298. 

[13] “帶你認識Vector-Quantized Variational AutoEncoder - 理論篇.” Medium, 28 April 2020, https://medium.com/ai-academy-taiwan/%E5%B8%B6%E4%BD%A0%E8%AA%8D%E8%AD%98vector-quantized-variational-autoencoder-%E7%90%86%E8%AB%96%E7%AF%87-49a1829497bb. 

[14] “VQ-VAE/VQGAN及改良工作小汇总.” 知乎专栏, 28 September 2022, https://zhuanlan.zhihu.com/p/569120964. 

[15] “What are Autoencoders?. 簡單介紹Autoencoder的原理，以及常見的應用。 | by Yu-Ru Tsai | Taiwan AI Academy.” Medium, 9 March 2019, https://medium.com/ai-academy-taiwan/what-are-autoencoders-175b474d74d1. 