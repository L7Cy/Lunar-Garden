---
title: timm
tags: 
aliases: [PyTorch Image Models]
---
- [GitHub - rwightman/pytorch-image-models: PyTorch image models, scripts, pretrained weights -- ResNet, ResNeXT, EfficientNet, EfficientNetV2, NFNet, Vision Transformer, MixNet, MobileNet-V3/V2, RegNet, DPN, CSPNet, and more](https://github.com/rwightman/pytorch-image-models)
- モデルのライブラリ
- 以下のようにするだけで，事前学習したモデルが読み込まれる
```python
model = timm.create_model('モデル名', pretrained=True)
```