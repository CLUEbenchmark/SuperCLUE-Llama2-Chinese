# SuperCLUE-Llama2-Chinese
Llama2中文版开源模型全方位测评，基于SuperCLUE基准



## 概要
Facebook母公司Meta发布了开源可商用的大模型Llama2，该开源模型受到广泛关注。Llama2为初创企业和其他企业提供了一个强大的免费选择。新版本Llama2将训练数据量增加了 40%，它包括70亿、130亿和700亿参数量的多个版本，此外还有对应的聊天机器人调优版本Llama 2-Chat。最近国内外大厂包括微软、阿里云等也宣布支持Llama2。开源社区和大量机构、个人，也纷纷着手基于Llama2构建中文版本及其应用。

基于Llama2的中文版本的效果怎么样？当前开源版本做到什么程度了；与国内代表性模型相比，特别是开源模型（baichuan-13b, chatglm2-6b）的相对表现如何；在一些比较关注的能力上，如生成与创作、逻辑推理、代码生成，表现怎么样呢？

基于SuperCLUE开放式与多轮测评基准（OPEN），即针对开放式的问题并结合多轮对话能力的测试，我们首次对Llama2中文版模型进行了定量和定性评估。通过前者可以看到模型的相对其他模型的表现，以及十大能力维度上的表现；而后者从一些典型示例中看到模型的表现（包括相对成熟和不足的能力）。


<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_chinese_v3.jpg"  width="90%" height="90%"></img>


## SuperCLUE开放式多轮测评-Llama2中文开源模型排行榜
| 序号 | 模型                                     | 机构 | OPEN分数 | 描述 |
|----|----------------------------------------|-|-|-|  
| -  | <a href='www.openai.com'>GPT-4</a>     | OpenAI | 94.64 | OpenAI发布的公认最强模型 |
| -  | <a href='https://www.anthropic.com/index/introducing-claude'>Claude-instant-v1</a>       | Authropic | 69.51 | OpenAI竞品的基础版本 |
| -  | <a href='https://huggingface.co/baichuan-inc/Baichuan-13B-Chat'>Baichuan-13B-chat</a>       | 百川智能 | 65.28 | 继7B之后的更大持续的模型,在高质量的语料上训练了 1.4 万亿 tokens,使用 ALiBi 位置编码,上下文窗口长度为 4096 |
| -  | <a href='https://huggingface.co/THUDM/chatglm2-6b'>ChatGLM2-6B</a>             | 清华&智谱AI | 36.50 | 第二代版本, 1.4T 中英标识符的预训练与人类偏好对齐训练, 结合FlashAttention 在8K上训练,更高效的推理 |
| 1  | <a href='https://huggingface.co/OpenBuddy/openbuddy-llama2-13b-v8.1-fp16'>openbuddy-llama2-13b</a>    | OpenBuddy | 35.12 | 多语言对话型人工智能,支持中文、英文、日文、韩文、法文、德文以及更多语言;增强词汇量和对常见CJK字符的支持。 |
| 2  | <a href='https://huggingface.co/meta-llama/Llama-2-13b-chat-hf'>Llama-2-13B-chat</a>        | Meta | 27.05 | Meta发布的原版Llama-2,主要支持英文,中文支持较弱 |  
| 3  | <a href='https://huggingface.co/FlagAlpha/Llama2-Chinese-13b-Chat'>Llama2-Chinese-13b-Chat</a> | Llama2中文社区(FlagAlpha) | 26.51 | 采用中文指令集,对Llama-2进行LoRA微调,使其具备较强的中文对话能力。 |
| 4  | <a href='https://huggingface.co/YeungNLP/firefly-llama2-13b'>firefly_llama2_13b</a>      | YeungNLP | 12.54 | 采用百万指令数据,对Llama-2进行QLoRA微调 |
| 5  | <a href='https://huggingface.co/FlagAlpha/Llama2-Chinese-7b-Chat'>Llama2-Chinese-7b-Chat</a>  | Llama2中文社区(FlagAlpha) | 12.50 | 采用中文指令集,对Llama-2进行LoRA微调,使其具备较强的中文对话能力。 |
| 6  | <a href='https://huggingface.co/wenge-research/yayi-13b-llama2'>yayi-13b-llama2</a>         | 中科闻歌(wenge-research,中科院自动化所孵化) | 8.78 | 在百万级人工构造的高质量领域数据上进行指令微调得到,训练数据覆盖媒体宣传、舆情分析、公共安全、金融风控、城市治理等五大领域,上百种自然语言指令任务。 |
