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

计算方法：
针对一个特定的开放式问题，利用超级模型作为评判官，计算被评估的模型相对于基线模型（如gpt-3.5）的胜、平局或失败的个数；
胜和率，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。win，即胜，tie即平，loss即负。

## SuperCLUE开放式多轮测评-十大能力，以Llama2中文版为例
| 序号 | 模型 | 胜和率 | 语义理解与抽取 | 闲聊 | 上下文对话 | 角色扮演 | 知识与百科 | 生成与创作 | 代码 | 逻辑与推理 | 计算 | 安全 |
|----|-|-|-|-|-|-|-|-|-|-|-|-|
| -  | gpt-4 | 94.64 | 80.00 | 97.30 | 93.18 | 100.00 | 87.76 | 100.00 | 97.92 | 100.00 | 100.00 | 95.12 |
| -  | Baichuan-13B-Chat | 65.28 | 45.00 | 88.33 | 78.33 | 91.67 | 55.00 | 91.67 | 25.00 | 50.88 | 35.71 | 81.67 | 
| -  | ChatGLM2-6B | 36.50 | 33.33 | 38.33 | 36.67 | 41.67 | 20.00 | 40.00 | 21.67 | 55.00 | 45.00 | 33.33 |
| 1  | openbuddy_llama2_13b | 35.12 | 33.33 | 40.00 | 23.33 | 20.00 | 23.33 | 46.67 | 33.33 | 58.62 | 50.00 | 23.33 |
| 2  | Llama-2-13B-chat | 27.05 | 43.33 | 35.00 | 27.12 | 11.67 | 15.00 | 46.67 | 6.67 | 35.00 | 26.67 | 23.33 |
| 3  | FlagAlpha-Llama2-13b-Chat | 26.51 | 33.33 | 36.67 | 36.67 | 24.14 | 10.00 | 50.00 | 6.67 | 41.38 | 13.33 | 13.33 |
| 4  | firefly_llama2_13b | 12.54 | 16.67 | 6.90 | 3.57 | 3.33 | 0.00 | 6.67 | 16.67 | 46.67 | 24.14 | 0.00 |
| 5  | FlagAlpha-Llama2-7b-Chat | 12.50 | 17.24 | 20.69 | 16.67 | 3.33 | 6.67 | 13.33 | 3.33 | 26.67 | 10.00 | 7.14 |
| 6  | yayi_13b_llama2 | 8.78 | 16.67 | 0.00 | 10.00 | 3.33 | 3.45 | 3.33 | 10.34 | 20.00 | 20.00 | 0.00 |
   
    胜和率，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。win，即胜，tie即平，loss即负。

## 当前Llama2开源中文版技术路线
1. 指令微调：根据已经开源的版本看，目前主要是基于Llama2进行指令微调。
2. 高效微调：目前普遍采用高效微调技术（如LoRA/QLoRA） 来微调大模型（如FlagAlpha, firefly_llama2_13b等）。
   这类技术上具备在单张GPU上微调大型语言模型的能力。LoRa为LLM的每一层添加了少量的可训练参数（适配器），并冻结了所有原始参数。
   这样对于微调，只需要更新适配器权重，这可以显著减少内存占用；QLoRA通过更高的量化（4-bit）和更多的可微调参数等进行改进。
3. 中文词汇表：部分模型（如openbuddy-llama2-13b）改进或扩充词汇表，实现中文上更好的支持。
4. 微调数据：使用百万微调数据进行微调，开源或构造特定领域数据（yayi）

## 初步结论
1. 基于SuperCLUE的OPEN基准，当前处于Llama2中文版的初级阶段，总体上模型质量参差不齐。
  在本次评估的5个模型中，在OPEN基准上有3个模型效果远远小于Llama2原版的效果（10多分 vs 27分）
2. 有部分模型取得不错的效果（如OpenBuddy），效果与ChatGLM2-6B接近（35.12 VS 36.50）；但与Baichuan-13B-Chat相比还有明显差距（35.12 VS 65.18）
3. 当前开源的Llama2中文模型与GPT3.5相比，差距巨大。最好模型与GPT3.5对战的胜率最高仅为12%，要达到接近的效果（如33%），还有很长的路要走。
4. 任务维度上，一些模型（openbuddy，FlagAlpha）具有还不错的生成与创作能力；并且在多种任务上都可以生成较长的回复，有些结构比较完整。

## 评估的不足与局限性
1. 它是一个自动化的模型能力测评，没有人类的主观因素；虽然加州伯克利大学/斯坦福大学的相关研究表明（见延伸阅读），
   自动化测评具有与人类评估的高度一致性（相关系数0.8-0.9），但进一步的分析还可以包括人类对模型的评估；
2. 评估的能力主要是基于SuperCLUE的十大基础能力，即使具有较高的代表性，但并不能保证覆盖了所有能力的评估。
3. 当前各个大模型厂商在快速迭代中，虽然我们报告的数字是最新的（7月中旬），但各个厂商的快速迭代可能会导致后续相对表现的进一步变化。
4. 在本文中，我们没有测试一些其他但有用的维度。比如，我们没有测试模型的性能问题（速度），也还没有测试模型的支持的有效的输入长度。后续可能会进行专门的测试。

## 延伸阅读
1. <a href='https://arxiv.org/abs/2307.15020'>SuperCLUE</a>: A Comprehensive Chinese Large Language Model Benchmark，
https://arxiv.org/abs/2307.15020
2. <a href='https://www.cluebenchmarks.com/superclue_open.html'>SuperCLUE-OPEN基准：中文通用大模型开放式与多轮测评基准（7月）</a>, https://www.cluebenchmarks.com/superclue_open.html
3. LMSYS文章：Chatbot Arena Leaderboard Week 8: Introducing MT-Bench and Vicuna-33B
4. 相关项目：Alpaca_Eval: A validated automatic evaluator for instruction-following language models
