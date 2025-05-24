# AI绘画的整合文档
网络上教程非常多，本文档是个人尝试之后的总结文档，以ComfyUI为例。未必面面俱到，需要有一定基础。

# Start

## 安装和配置
1. github链接clone
2. 配置环境

## 模型

### 基座模型checkpoint
C站（Civitai）、Huggingface上有非常多基座模型，自己喜欢的才是最好的，动漫风格推荐：
- https://civitai.com/models/833294/noobai-xl-nai-xl
- https://civitai.com/models/827184/wai-nsfw-illustrious-sdxl

真人风格推荐:
- https://huggingface.co/black-forest-labs/FLUX.1-dev

### 微调模型lora（非必要）
1. C站（Civitai）

## 工作流
ComfyUI本身提供很多预设工作流，社区也有许多工作流可供下载。在`workflows`中提供了基础的工作流，在ComfyUI中加载即可。

# 参考指南
1. Noob画师风格法典
   - https://docs.qq.com/sheet/DZGxRSXhvcmNmeHFv?tab=zg6fob
2. 画师法典
   - https://docs.qq.com/sheet/DSUd5eGRCZ0tFcGZJ?tab=BB08J2
3. NoobAI指南
   - https://fcnk27d6mpa5.feishu.cn/wiki/S8Z4wy7fSiePNRksiBXcyrUenOh
4. NoobAI画师风格推荐
   - https://fcnk27d6mpa5.feishu.cn/wiki/IBVGwvVGViazLYkMgVEcvbklnge
5. NoobAI-XL用户手册
   - https://d0xb9r3fg5h.feishu.cn/docx/WWOHdr6RMoQZxQxCZRGc5KlEnUi
6. 个人总结
   - https://docs.qq.com/sheet/DZGZhYU9mT1dQaGdT

# Environment Variables

The following features can be configured using environment variables:

* **COMFYUI_PATH**: The installation path of ComfyUI
* **GITHUB_ENDPOINT**: Reverse proxy configuration for environments with limited access to GitHub
* **HF_ENDPOINT**: Reverse proxy configuration for environments with limited access to Hugging Face


## Example 1:
Redirecting `https://github.com/ltdrdata/ComfyUI-Impact-Pack` to `https://mirror.ghproxy.com/https://github.com/ltdrdata/ComfyUI-Impact-Pack`

```
GITHUB_ENDPOINT=https://mirror.ghproxy.com/https://github.com
```

## Example 2:
Changing `https://huggingface.co/path/to/somewhere` to `https://some-hf-mirror.com/path/to/somewhere`

```
HF_ENDPOINT=https://some-hf-mirror.com 
```

## 3DPoseEditor插件
1. 关于插件使用的模型b站`BV1wf421i7N7`有讲
2. 关于框架错位
```
插件目录找到openposeeditor.js打开，找到
left: `${transform.a * margin + transform.e }px`,
top: `${transform.d + transform.f + top_offset}px`,
这两行各加65px保存就行。
改完的样子：
left: `${transform.a * margin + transform.e + 65}px`,
top: `${transform.d + transform.f + top_offset + 65}px`,
```