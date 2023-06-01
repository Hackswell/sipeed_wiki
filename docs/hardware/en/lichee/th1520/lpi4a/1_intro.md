---
title: Update History
keywords: Linux, Lichee, Lichee Pi 4A, TH1520, C910, SBC, RISCV
updates:
  - date: 2023-06-01
    version: v1.0.1
    author: hackswell
    content: Start editing EN version of documentation

  - date: 2023-05-08
    version: v1.0
    author: wonder
    content: Release docs
---

English documents are currently being translated, please read these documents via web translate application at present if necessary.

## Introduction

LicheePi 4A is a high-performance RISC-V Linux development board based on the [Lichee Module 4A](http://wiki.sipeed.com/hardware/zh/lichee/th1520/lm4a.html) core board, with [TH1520](https://www.t-head.cn/product/yeying) as the main control core (4xC910@1.85G, RV64GCV, 4TOPS@int8 NPU, 50GFLOP GPU), the maximum onboard 16GB 64bit LPDDR4X, 128GB eMMC, supports HDMI+MIPI dual 4K display output, supports 4K camera access, dual Gigabit Ethernet ports (one of which supports POE power supply) and 4 USB3.0 ports, multiple audio input and output (processed by a dedicated C906 core).

![lpi4a](./../../../../zh/lichee/th1520/lpi4a/assets/intro/lpi4a.png)

LicheePi 4A is the strongest RISC-V SBC so far (2023Q2). The performance is about twice that of the previous generation RISC-V SBC [VisionFive2](https://www.starfivetech.com/en/site/boards); without special instruction set acceleration, the performance is close to that of the ARM A72-based Raspberry Pi 4, and when the relevant instruction set acceleration is enabled, it can be compared with the Raspberry Pi 4 is even. And it has a maximum of 16GB of large memory, which is twice the maximum configuration of Raspberry Pi 4 with 8GB of memory!

![benchmark](./../../../../zh/lichee/th1520/lpi4a/assets/intro/benchmark.png)
![geekbench5](./../../../../zh/lichee/th1520/lpi4a/assets/intro/geekbench5.png)
 
LicheePi 4A can be used as a typical RISC-V verification platform, and its powerful performance can realize local compilation relatively quickly without using QEMU for compilation.

In the near future (2023Q2), we will also release the LM4A-based cluster computing board LicheeCluster 4A, which supports up to 7xLM4A for cluster computing and compilation.

While maintaining high performance, we have also implemented CostDown design as much as possible. The price of the 8GB memory version is ￥749 ~ 899 (US$100 ~ $130), and the 16GB memory version is ￥1100 ~ 1300 (US$155 ~ $185), cost-effective Beyond the Raspberry Pi 4 (8GB ~ US$150)!
Whether you are a RISC-V fan or not, you are worth starting to experience LicheePi 4A, an epoch-making high-performance RISC-V SBC!

![desktop](./../../../../zh/lichee/th1520/lpi4a/assets/intro/desktop.png)

## Contributions are welcome
This document is an online document hosted on github. You can click the `编辑本页` link to edit it~
For users who successfully submit the document, we will provide ￥5 ~ 150 (US$1 ~ $20) coupons depending on the quality of the document~

## Basic parameters
<table>
<thead>
<tr>
  <th colspan=2>Main Specifications</th>
</tr>
</thead>
<tbody>
<tr>
  <td>Chipset</td>
  <td>TH1520</td>
</tr>
<tr>
  <td>CPU</td>
  <td>RISC-V 64GCV C910*4@2GHz<br>
    · Each core supports 64KB Iicache and 64KB D-cache<br>
    · All four cores share 1MB L2 Cache<br>
    · Supports TEE and REE，TEE/REE supports core number configurable at startup<br>
    · Supports customization and interface compatibility with RISC-V multi-core debugging framework<br>
    · Independent power domain, supports DVFS</td>
</tr>
<tr>
  <td>GPU</td>
  <td>· OpenCL 1.1/1.2/2.0<br>
    · OpenGL ES 3.0/3.1/3.2<br>
    · Vulkan 1.1/1.2<br>
    · Android NN HAL</td>
</tr>
<tr>
  <td>Neural Processing Unit<br>(NPU)</td>
  <td>· Supports 4TOPS@INT8 general-purpose NNA computing power, clock frequency 1GHz<br>
    · Supports TensorFlow, ONNX, Caffe<br>
    · Supports CNN, RNN, DNN, etc.</td>
</tr>
<tr>
  <td>Video Codecs</td>
  <td>· Real-time decoder supports: H.265/H.264/VP9/8/7/6/AVS/AVS+/AVS2.0/VC1/MPEG4<br>
    · H.264 BP/MP/HP@level 5.1 decoding, maximum 4K resolution<br>
    · H.265/HEVC Main Profile@level 5.1 decoding, maximum 4K resolution<br>
    · VP9 Profile-2 decoding, maximum 4K resolution<br>
    · AVS2.0 decoding, maximum 4K resolution<br>
    · VP6/7/8/AVS/AVS+/VC1/MPEG4 decoding, maximum 1920x1080 resolution<br>
    · Maximum decoding performance: 4K@75fps</td>
</tr>
<tr>
  <td>Video Encoder</td>
  <td>· H.264 BP/MP/HP@level4.2 encoding, maximum 4K resolution<br>
    · H.265/HEVC Main Profile encoding, maximum 4K resolution<br>
    · Only supports I-frame and P-frame<br>
    · Maximum encoding performance: 4K@40fps</td>
</tr>
<tr>
  <th colspan=2>Hardware Features</th>
</tr>
<tr>
  <td>RAM</td>
  <td>· 64bits LPDDR4: 8GB or 16GB<br></td>
</tr>
<tr>
  <td>Storage</td>
  <td>· eMMC options: none, 8G, 32G, or 128G<br>
    · TF card support</td>
</tr>
<tr>
  <td>Ethernet</td>
  <td>· 2 x Gigabit Ethernet ports, optional POE</td>
</tr>
<tr>
  <td>USB</td>
  <td>· USB3.0 x 4<br>
    · USB2.0 x 1（for programming only）</td>
</tr>
<tr>
  <td>Audio Ports</td>
  <td>· 1 x 3.5mm headphone jack<br>
    · One speaker jack<br>
    · Two onboard microphones</td>
</tr>
<tr>
  <td>Display Ports</td>
  <td>· 1 x HDMI2.0<br>
    · 1 x 4-lane MIPI DSI</td>
</tr>
<tr>
  <td>Camera Interfaces</td>
  <td>· 2 x 2-lane MIPI CSI<br>
    · 1 x 4-lane MIPI CSI</td>
</tr>
<tr>
  <td>GPIO</td>
  <td>· UART<br>
    · IIC<br>
    · SPI</td>
</tr>
</tbody>
</table>

### Hardware Data Downloads

[Board Specifications](https://dl.sipeed.com/shareURL/LICHEE/licheepi4a/01_Specification)

[Backplane Schematic](https://dl.sipeed.com/shareURL/LICHEE/licheepi4a/02_Schematic)

[Backplane point and bitmap](https://dl.sipeed.com/shareURL/LICHEE/licheepi4a/03_Bit_number_map)

[Backplane dimension](https://dl.sipeed.com/shareURL/LICHEE/licheepi4a/04_Dimensional_drawing)

[Model file](https://dl.sipeed.com/shareURL/LICHEE/licheepi4a/05_3D_model)

## Other Links

Online store: [Aliexpress](https://www.aliexpress.com/item/1005005532736080.html)

[Github](https://github.com/sipeed/LicheePi4A)

[Sipeed download site](https://dl.sipeed.com/shareURL/LICHEE/licheepi4a)

Telegram: https://t.me/linux4rv

Contact email：support@sipeed.com
