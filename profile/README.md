<!-- markdownlint-disable first-line-h1 -->
<!-- markdownlint-disable html -->
<div align="center">
<h1>
  Sakura-13B-Galgame
</h1>
</div>

<p align="center">
  🤗 <a href="https://huggingface.co/sakuraumi/Sakura-13B-Galgame" target="_blank">Hugging Face</a> • 🤖 <a href="https://www.modelscope.cn/models/sakuraumi/Sakura-13B-Galgame" target="_blank">ModelScope</a>
</p>

# 介绍

基于OpenBuddy(v0.1-v0.4), Qwen-14B(v0.7,v0.9)和Baichuan2-13B(v0.5,v0.8)构建，在通用日文语料与轻小说/Galgame等领域的中日语料上进行微调，旨在提供性能接近GPT3.5且完全离线的Galgame/轻小说翻译大语言模型. 新建了[TG交流群](https://t.me/+QMDKZyO9GV1kNDA1)，欢迎交流讨论。

**如果使用模型翻译并发布，请在最显眼的位置标注机翻！！！！！开发者对于滥用本模型造成的一切后果不负任何责任。**

### 快速开始
 - [python部署教程](https://sakura.srpr.moe)
 - [llama.cpp一键包教程](https://books.fishhawk.top/forum/656d60530286f15e3384fcf8)
 - [autodl租显卡部署教程](https://books.fishhawk.top/forum/65719bf16843e12bd3a4dc98)

### News

1. 预览版v0.9.0pre2模型发布。该版本模型只是预览版本，目前可能仍存在问题。修复了上一预览版本短文本退化的问题。

2. **网站：[轻小说机翻机器人](https://books.fishhawk.top/)已接入Sakura模型(v0.8-4bit)，站内有大量模型翻译结果可供参考。你也可以自行部署模型并使用该网站生成机翻，目前已经支持v0.8与v0.9模型，且提供了llama.cpp一键包。**
  
   轻小说机翻机器人网站是一个自动生成轻小说机翻并分享的网站。你可以浏览日文网络小说，或者上传Epub/Txt文件，并生成机翻。

3. **[LunaTranslator](https://github.com/HIllya51/LunaTranslator)已经支持Sakura API，可以通过本地部署API后端，并在LunaTranslator中配置Sakura API来使用Sakura模型翻译Galgame。**

   LunaTranslator是一个Galgame翻译工具，支持剪贴板、OCR、HOOK，支持40余种翻译引擎。

### 模型下载：
|   版本  | 全量模型 | 8-bit量化 | 4-bit量化 | 3-bit量化 | GGUF | AWQ
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|
| 20231026-v0.8 | 🤗 [Sakura-13B-LNovel-v0.8](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.8) | 🤗 [Sakura-13B-LNovel-v0_8-8bit](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-8bit) | 🤗 [Sakura-13B-LNovel-v0_8-4bit](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-4bit) | 🤗 [Sakura-13B-LNovel-v0_8-3bit](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-3bit) | 🤗 [Sakura-13B-LNovel-v0_8-GGUF](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.8-GGUF) | 🤗 [Sakura-13B-LNovel-v0_8-AWQ](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-AWQ) |
| 20231125-v0.9.0pre1 | 🤗 [Sakura-13B-LNovel-v0.9.0pre1](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.9.0pre1) | - | - | - | 🤗 [Sakura-13B-LNovel-v0.9.0pre1-GGUF](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.9.0pre1-GGUF) | - |
| 20231125-v0.9.0pre2 | - | - | - | - | 🤗 [Sakura-13B-LNovel-v0.9.0pre1-GGUF](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.9.0pre2-GGUF) | - |

目前仍为实验版本，翻译质量在文风与流畅度上强于GPT-3.5，但词汇量逊于GPT-3.5. 个人使用推荐GPT4.

# 显存需求

下面的表格显示了使用不同量化和不同格式的模型时显存占用的大小。如果你的显卡显存不满足上述需求，可以尝试同时使用CPU与GPU进行推理。

- llama.cpp GGUF模型（使用v0.9.0pre1模型进行测试，v0.8模型与其类似）

|  模型量化类型  | 模型大小 | 推荐显存大小 |
|:-------:|:-------:|:-------:|
| fp16 | 26.3G | 超出游戏显卡显存范围 |
| Q8_0 | 14G | 24G |
| Q6_K | 11.4G | 20G |
| Q5_K_M | 10.1G | 16G |
| Q4_K_M | 8.8G | 16G |
| Q3_K_M | 7.2G | 16G |
| Q2_K | 6.1G | 12G |

- transformers autogptq模型（使用v0.8版本进行测试）

|  模型量化类型 | 推理显存(ctx约600) | 推理显存(ctx约1800) |
|:-------:|:-------:|:-------:|
| 全量 | 超出游戏显卡显存范围  | 超出游戏显卡显存范围  |
| 8bit | 21.1G | 23.4G |
| 4bit | 14.9G | 17.4G |
| 3bit | 13.7G | 15.5G |


# 更多信息
详情请查看[此页面](https://github.com/SakuraLLM/Sakura-13B-Galgame)
