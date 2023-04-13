
#  Stable Diffusion
2022 年发布的稳定扩散（Stable Diffusion） 是一个文本到图像生成的深度学习模型。

# Stable Diffusion web UI
Stable Diffusion web UI：基于 Gradio 开发的浏览器界面。提供了众多实用功能，支持插件，强烈推荐。

- Prompt 输入框：输入提示，即需要生成图片的文字描述，一般为英文短句或单词，以逗号进行分隔。

- Negative Prompt 输入框：除了一些功能阉割网站不支持此功能外，Stable Diffusion 早期版本也不支持。否定提示也是一种输入提示，用来指定生成的图像中不应包含的内容。这些提示可用于微调模型的输出并确保它不会生成包含某些元素或特征的图像（达到过滤的目的）。和提示用法一样，以逗号进行分隔。（注意：否定提示可以阻止生成特定的事物、样式或修复某些图像异常，但并非 100% 有效）

- Generate image 按钮：提示输入完成后，点击此按钮则开始生成图片。

- 图片展示区：此区域用来展示图片生成后的结果。

仓库地址：https://github.com/AUTOMATIC1111/stable-diffusion-webui
在线地址：https://huggingface.co/spaces/stabilityai/stable-diffusion

Mac安装方法：https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon


在项目根路径下找到 webui.sh，通过命令行来运行它。
它会自动下载相关依赖并启动一个服务。默认 URL 为 http://127.0.0.1:7860。

# 模型
下载模型必逛的两个网站：
- C 站: https://civitai.com
- HuggingFace: https://huggingface.co

C 站有大量的 lora 微调模型可以选择，HuggingFace 上可以直接搜索到很多 sd 相关模型（比如直接搜：stable-）

# prompt

```text
<lora:cheeseDaddys_35:0.8>, masterpiece, best quality, high quality, extremely detailed CG unity 8k wallpaper, classical chinese, [dark night, shooting star, flower], fair face, and beautiful watery eyes, dynamic cinematic lighting, aesthetic, female, ponytail, smile, award winning photography, Bokeh, Depth of Field, HDR, High Detail, dramatic, art by midjourney,
Negative prompt: 
fat, ugly, tiling, poorly drawn hands, poorly drawn feet, poorly drawn face, out of frame, extra limbs, disfigured, deformed, body out of frame, bad anatomy, watermark, signature, cut off, low contrast, underexposed, overexposed, bad art, beginner, amateur, distorted face,
Steps: 28, 
Sampler: DPM++ 2S a Karras, 
CFG scale: 7, 
Seed: 84858658625, 
Size: 1024x1024, 
Model: yesmix_v16Original, 
Denoising strength: 0.68
```


#名词解释
LoRA 模型（LoRA: Low-Rank Adaptation of Large Language Models[36]）：LoRA 是一种在大型语言模型的预训练权重基础上，注入可训练秩分解矩阵，从而减少可训练参数数量，提高训练吞吐量和减少 GPU 内存需求的方法。相比于完全微调模型，LoRA 可以在不增加推理延迟的情况下，达到相当甚至更好的模型性能（简单来说它就是基础模型的微调模型，比如修改风格为国风，水墨风等）。

VAE（Variational Autoencoder[37]）：VAE 代表变分自动编码器。它是神经网络模型的一部分，可对来自较小潜在空间的图像进行编码和解码（极大减少了显存），从而使计算速度更快。

Model 与 Lora 的关系（以书本世界为例）：

Model：百科全书

LoRA: 百科全书中的一个额外条目，作为一个“便利贴”塞进其中。

.ckpt 与 .safetensors：它们都是一种用于分发模型的文件格式。

.ckpt：是很多包含 Python 代码的压缩文件，利用它们就像解压缩一样简单。因包含大量代码，意味着它可能包含恶意代码，加载未知不信任来源的 .ckpt 文件，很可能会危害你的计算机。

.safetensors：只包含生成所需的数据，更难被利用。不包含代码，所以加载 .safetensors 文件也更安全和快速。