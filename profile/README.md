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

- 基于一系列开源大模型构建，在通用日文语料与轻小说/Galgame等领域的中日语料上进行继续预训练与微调，旨在提供性能接近GPT3.5且完全离线的Galgame/轻小说翻译大语言模型。
  
- 目前仍为实验版本，v0.9版本模型在文风、流畅度与准确性上均强于GPT-3.5，但词汇量略逊于GPT-3.5（主观评价）.

- 同时提供了运行模型的API后端，适配OpenAI API格式。

- 新建了[TG交流群](https://t.me/+QMDKZyO9GV1kNDA1)，欢迎交流讨论。

**如果使用模型翻译并发布，请在最显眼的位置标注机翻！！！！！开发者对于滥用本模型造成的一切后果不负任何责任。**

**对于模型翻译的人称代词问题（错用，乱加，主宾混淆，男女不分等）和上下文理解问题，如果有好的想法或建议，欢迎提issue！**

## 快速开始

### 教程：

详见[本仓库Wiki](https://github.com/SakuraLLM/Sakura-13B-Galgame/wiki).

### 模型下载：

|   版本  | Transformers模型 | GGUF量化模型 | GPTQ 8bit量化 | GPTQ 4bit量化 | GPTQ 3bit量化 | AWQ量化
|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|:-------:|
| 20231026-v0.8 | 🤗 [Sakura-13B-LNovel-v0.8](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.8) | 🤗 [Sakura-13B-LNovel-v0_8-GGUF](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.8-GGUF) | 🤗 [Sakura-13B-LNovel-v0_8-8bit](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-8bit) | 🤗 [Sakura-13B-LNovel-v0_8-4bit](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-4bit) | 🤗 [Sakura-13B-LNovel-v0_8-3bit](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-3bit) | 🤗 [Sakura-13B-LNovel-v0_8-AWQ](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0_8-AWQ) |
| 20240111-v0.9 | 🤗 [Sakura-13B-LNovel-v0.9](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.9) | 🤗 [Sakura-13B-LNovel-v0.9-GGUF](https://huggingface.co/SakuraLLM/Sakura-13B-LNovel-v0.9-GGUF) | - | - | - | - |

## News

1.  **更新了0.9的第一个正式版模型`v0.9`。修复若干bug，清洗并增加了预训练与微调的数据量。更推荐使用正式版模型，它会比之前的pre版本更加稳定，质量更高。**

1.  感谢[Isotr0py](https://github.com/Isotr0py)提供运行模型的NoteBook仓库[SakuraLLM-Notebooks](https://github.com/Isotr0py/SakuraLLM-Notebooks)，可在[Colab](https://colab.research.google.com/)(免费T4\*1)与[Kaggle](https://www.kaggle.com/)(免费P100\*1或T4\*2)平台使用。**已经更新Kaggle平台的[使用教程](https://github.com/SakuraLLM/Sakura-13B-Galgame/wiki/%E7%99%BD%E5%AB%96Kaggle%E5%B9%B3%E5%8F%B0%E9%83%A8%E7%BD%B2%E6%95%99%E7%A8%8B)，可以白嫖一定时间的T4\*2。**

1.  **Sakura API已经支持OpenAI格式，现在可以通过OpenAI库或者OpenAI API Reference上的请求形式与Server交互。**
一个使用OpenAI库与Sakura模型交互的例子详见[openai_example.py](https://github.com/SakuraLLM/Sakura-13B-Galgame/blob/main/tests/example_openai.py)。

## 已经接入模型的工具

1. 网站：[轻小说机翻机器人](https://books.fishhawk.top/)已接入Sakura模型(v0.8-4bit)，站内有大量模型翻译结果可供参考。你也可以自行部署模型并使用该网站生成机翻，目前已经支持v0.8与v0.9模型，且提供了llama.cpp一键包。
  
   轻小说机翻机器人网站是一个自动生成轻小说机翻并分享的网站。你可以浏览日文网络小说，或者上传Epub/Txt文件，并生成机翻。

1. [LunaTranslator](https://github.com/HIllya51/LunaTranslator)已经支持Sakura API，可以通过本地部署API后端，并在LunaTranslator中配置Sakura API来使用Sakura模型进行Galgame实时翻译。

   LunaTranslator是一个Galgame翻译工具，支持剪贴板、OCR、HOOK，支持40余种翻译引擎。

1. [GalTransl](https://github.com/XD2333/GalTransl)已经支持Sakura API，可以通过本地部署API后端，在GalTransl中配置使用Sakura模型来翻译Galgame，制作内嵌式翻译补丁。

   GalTransl是一个galgame自动化翻译工具，用于制作内嵌式翻译补丁。一个使用GalTransl和Sakura模型翻译的[示例](https://www.ai2moe.org/files/file/2271-%E6%88%AF%E7%94%BBgaltranslsakuragpt35%E7%88%B1%E4%B9%8B%E5%90%BB3-sexy-gpt%E7%BF%BB%E8%AF%91%E8%A1%A5%E4%B8%81uploadee5-mb/)

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
