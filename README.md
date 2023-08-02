# SuperCLUE-Llama2-Chinese
Llama2中文版开源模型全方位测评，基于SuperCLUE基准



## 概要
Facebook母公司Meta发布了开源可商用的大模型Llama2，该开源模型受到广泛关注。Llama2为初创企业和其他企业提供了一个强大的免费选择。新版本Llama2将训练数据量增加了 40%，它包括70亿、130亿和700亿参数量的多个版本，此外还有对应的聊天机器人调优版本Llama 2-Chat。最近国内外大厂包括微软、阿里云等也宣布支持Llama2。开源社区和大量机构、个人，也纷纷着手基于Llama2构建中文版本及其应用。

基于Llama2的中文版本的效果怎么样？当前开源版本做到什么程度了；与国内代表性模型相比，特别是开源模型（baichuan-13b, chatglm2-6b）的相对表现如何；在一些比较关注的能力上，如生成与创作、逻辑推理、代码生成，表现怎么样呢？

基于SuperCLUE开放式与多轮测评基准（OPEN），即针对开放式的问题并结合多轮对话能力的测试，我们首次对Llama2中文版模型进行了定量和定性评估。通过前者可以看到模型的相对其他模型的表现，以及十大能力维度上的表现；而后者从一些典型示例中看到模型的表现（包括相对成熟和不足的能力）。

## update
[2023-08-02] 添加  <a href='https://huggingface.co/ziqingyang/chinese-alpaca-2-7b'>Chinese-Alpaca-2-7B</a>

<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_chinese_v3.jpg"  width="90%" height="90%"></img>


## SuperCLUE开放式多轮测评-Llama2中文开源模型排行榜
| 排名 | 模型                                                                                                   | 机构                             | OPEN分数 | 描述                                                                                           |
|:---|:-----------------------------------------------------------------------------------------------------|:-------------------------------|:-------|:---------------------------------------------------------------------------------------------|  
| -  | <a href='www.openai.com'>GPT-4</a>                                                                   | OpenAI                         | 94.64  | OpenAI发布的公认最强模型                                                                              |
| -  | <a href='https://www.anthropic.com/index/introducing-claude'>Claude-instant-v1</a>                   | Authropic                      | 69.51  | OpenAI竞品的基础版本                                                                                |
| -  | <a href='https://huggingface.co/baichuan-inc/Baichuan-13B-Chat'>Baichuan-13B-chat</a>                | 百川智能                           | 65.28  | 继7B之后的更大持续的模型,在高质量的语料上训练了 1.4 万亿 tokens,使用 ALiBi 位置编码,上下文窗口长度为 4096                          |
| -  | <a href='https://huggingface.co/THUDM/chatglm2-6b'>ChatGLM2-6B</a>                                   | 清华&智谱AI                        | 36.50  | 第二代版本, 1.4T 中英标识符的预训练与人类偏好对齐训练, 结合FlashAttention 在8K上训练,更高效的推理                               |
| 1  | <a href='https://huggingface.co/OpenBuddy/openbuddy-llama2-13b-v8.1-fp16'>openbuddy-llama2-13b</a>   | OpenBuddy                      | 35.12  | 多语言对话型人工智能,支持中文、英文、日文、韩文、法文、德文以及更多语言;增强词汇量和对常见CJK字符的支持。                                      |
| 2  | <a href='https://huggingface.co/meta-llama/Llama-2-13b-chat-hf'>Llama-2-13B-chat</a>                 | Meta                           | 27.05  | Meta发布的原版Llama-2,主要支持英文,中文支持较弱                                                               |  
| 3  | <a href='https://huggingface.co/FlagAlpha/Llama2-Chinese-13b-Chat'>Llama2-Chinese-13b-Chat</a>       | Llama2中文社区(FlagAlpha)          | 26.51  | 采用中文指令集,对Llama-2进行LoRA微调,使其具备较强的中文对话能力。                                                      |
| 4  | <a href='https://huggingface.co/ziqingyang/chinese-alpaca-2-7b'>Chinese-Alpaca-2-7B</a>              | ymcui                        | 14.43  | 扩充并优化了中文词表，使用了大规模中文数据进行增量预训练(120G)，基于FlashAttention-2的高效注意力训练,相关模型支持4K上下文并可通过NTK方法最高扩展至18K+。 |
| 5  | <a href='https://huggingface.co/YeungNLP/firefly-llama2-13b'>firefly_llama2_13b</a>                  | YeungNLP                       | 12.54  | 采用百万指令数据,对Llama-2进行QLoRA微调                                                                   |
| 6  | <a href='https://huggingface.co/FlagAlpha/Llama2-Chinese-7b-Chat'>Llama2-Chinese-7b-Chat</a>         | Llama2中文社区(FlagAlpha)          | 12.50  | 采用中文指令集,对Llama-2进行LoRA微调,使其具备较强的中文对话能力。                                                      |
| 7  | <a href='https://huggingface.co/wenge-research/yayi-13b-llama2'>yayi-13b-llama2</a>                  | 中科闻歌(wenge-research,中科院自动化所孵化) | 8.78   | 在百万级人工构造的高质量领域数据上进行指令微调得到,训练数据覆盖媒体宣传、舆情分析、公共安全、金融风控、城市治理等五大领域,上百种自然语言指令任务。                   |


计算方法：
针对一个特定的开放式问题，利用超级模型作为评判官，计算被评估的模型相对于基线模型（如gpt-3.5）的胜、平局或失败的个数；
胜和率，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。win，即胜，tie即平，loss即负。

## SuperCLUE开放式多轮测评-十大能力，以Llama2中文版为例
| 排名 | 模型                        | 胜和率   | 语义理解与抽取 | 闲聊    | 上下文对话 | 角色扮演   | 知识与百科 | 生成与创作  | 代码    | 逻辑与推理  | 计算     | 安全    |
|:---|:--------------------------|:------|:--------|:------|:------|:-------|:------|:-------|:------|:-------|:-------|:------|
| -  | gpt-4                     | 94.64 | 80.00   | 97.30 | 93.18 | 100.00 | 87.76 | 100.00 | 97.92 | 100.00 | 100.00 | 95.12 |
| -  | Baichuan-13B-Chat         | 65.28 | 45.00   | 88.33 | 78.33 | 91.67  | 55.00 | 91.67  | 25.00 | 50.88  | 35.71  | 81.67 | 
| -  | ChatGLM2-6B               | 36.50 | 33.33   | 38.33 | 36.67 | 41.67  | 20.00 | 40.00  | 21.67 | 55.00  | 45.00  | 33.33 |
| 1  | openbuddy_llama2_13b      | 35.12 | 33.33   | 40.00 | 23.33 | 20.00  | 23.33 | 46.67  | 33.33 | 58.62  | 50.00  | 23.33 |
| 2  | Llama-2-13B-chat          | 27.05 | 43.33   | 35.00 | 27.12 | 11.67  | 15.00 | 46.67  | 6.67  | 35.00  | 26.67  | 23.33 |
| 3  | FlagAlpha-Llama2-13b-Chat | 26.51 | 33.33   | 36.67 | 36.67 | 24.14  | 10.00 | 50.00  | 6.67  | 41.38  | 13.33  | 13.33 |
 | 4  |    Chinese-Alpaca-2-7B	       | 14.43  | 20.00   | 6.67  | 20.00 | 10.34  | 6.67  | 3.33   | 10.00 | 37.93  | 30.00  | 0.00  |
| 5  | firefly_llama2_13b        | 12.54 | 16.67   | 6.90  | 3.57  | 3.33   | 0.00  | 6.67   | 16.67 | 46.67  | 24.14  | 0.00  |
| 6  | FlagAlpha-Llama2-7b-Chat  | 12.50 | 17.24   | 20.69 | 16.67 | 3.33   | 6.67  | 13.33  | 3.33  | 26.67  | 10.00  | 7.14  |
| 7  | yayi_13b_llama2           | 8.78  | 16.67   | 0.00  | 10.00 | 3.33   | 3.45  | 3.33   | 10.34 | 20.00  | 20.00  | 0.00  |
  
    胜和率，是模型的胜率加上平局率之和，即(win+tie)/(win+tie+loss)*100。win，即胜，tie即平，loss即负。

在SuperCLUE开放式多轮测评-十大能力成绩评估中，我们发现Llama2中文模型在多数任务上效果总体效果还比较一般，多数能力的平均分离及格线都有比较大的差距。

## 定性分析
### 1）基础能力的例子
#### 生成与创作
  生成与创作，比如给定一个话题、一个写作任务来创作一段文字对于LLMs而言是相对比较容易的任务。
  我们发现作为中文llama-2微调模型中的佼佼者， OpenBuddy生成的内容在结构性、丰富度上距离百川13b仍有不小的差距，并且openbuddy的形容过于宽泛而缺少具体例子，
  有些词汇使用的也不太合适，比如用敏锐描述幽默感便有些不恰当。
<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_1.png"  width="90%" height="90%"></img>


#### 语义理解与抽取
  openbuddy能精确地理解用户的意图完成任务，但是从返回的内容本身以及格式上来说openbuddy输出的内容不如百川的好。<br/>

<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_2.png"  width="90%" height="90%"></img>

### 2）上下文能力的例子
  在两轮对话的测试中，两个模型都能正确的完成任务。
  在我们给出的示例中，openbuddy在第一轮的回答中给出的建议不如百川13b给出的建议充分，但两者的回答结构都非常优秀，让用户能有不错的体验。在第二轮对话中，虽然openbuddy修改了自己的回答，但是相比百川，其修改的幅度较小，很大比例是照搬上一轮的回答。
<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_3.png"  width="90%" height="90%"></img>

<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_4.png"  width="90%" height="90%"></img>

### 3）复杂任务（逻辑推理、代码生成、思维链路等）的例子
#### 代码生成
  代码，属于百川和openbuddy都不擅长的领域。和我们在百川测评推文中提到的一样，在我们给出的示例中，百川虽然能完成任务，但是给出的代码完全没考虑到非整数元素不需要逆转。  至于openbuddy，其虽然理解了用户仅将整数逆转的需求，但是给出的代码仅仅是把原列表中的整数按顺序放入新列表返回，并且给出的示例也和其给出的代码的实际效果不一致。
<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_5.png"  width="90%" height="90%"></img>

  回顾我们上一篇的推文，可以发现Llama-2-13B-chat本身也会出现给出的代码与给出的代码用例不一致的情况。
<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_6.png"  width="90%" height="90%"></img>

#### 逻辑推理
  逻辑推理，同样属于百川和openbuddy都不擅长的领域。两者对问题的回答都是错误的。其中openbuddy的回答更显混乱一些，不仅没能正确理解问题，而且出现了许多非常初等的计算错误，比如4-2-4=0这种错误回答。两个模型都在回答时搞错了卡牌的总数，而我们在问题中是明确指出总共有十张卡牌的。
正确答案是4张绿色背景卡牌
<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_7.png"  width="90%" height="90%"></img>

  回顾Llama-2-13B-chat可以看到，Llama-2-13B-chat同样无法给出正确答案。
<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_8.png"  width="90%" height="90%"></img>


## 当前Llama2开源中文版如何实现的？
1. 指令微调：根据已经开源的版本看，目前主要是基于Llama2进行指令微调。
2. 高效微调：目前普遍采用高效微调技术（如LoRA/QLoRA） 来微调大模型（如FlagAlpha, firefly_llama2_13b等）。
   这类技术上具备在单张GPU上微调大型语言模型的能力。LoRa为LLM的每一层添加了少量的可训练参数（适配器），并冻结了所有原始参数。
   这样对于微调，只需要更新适配器权重，这可以显著减少内存占用；QLoRA通过更高的量化（4-bit）和更多的可微调参数等进行改进。
3. 中文词汇表：部分模型（如openbuddy-llama2-13b）改进或扩充词汇表，实现中文上更好的支持。
4. 微调数据：使用百万微调数据进行微调，开源或构造特定领域数据（yayi）

## 初步结论
1. 整体质量：基于SuperCLUE的OPEN基准，当前处于Llama2中文版的初级阶段，总体上模型质量参差不齐。
   在本次评估的5个模型中，在OPEN基准上有3个模型效果远远小于Llama2原版的效果（10多分 vs 27分）
2. 存在不错模型：有部分模型取得不错的效果（如OpenBuddy），效果与ChatGLM2-6B接近（35.12 VS 36.50）；但与Baichuan-13B-Chat相比还有明显差距（35.12 VS 65.18）
3. 与先进模型差距大：开源Llama2中文模型中，OpenBuddy与GPT3.5对战的胜率最高，但仅为12%，要达到接近GPT3.5的效果（胜率提升至33%），还有很长的路要走。
4. 部分任务已经有效果：任务维度上，一些模型（openbuddy，FlagAlpha）具有还不错的生成与创作能力；并且在多种任务上都可以生成较长的回复，有些结构比较完整。

## 评估的不足与局限性
1. 它是一个自动化的模型能力测评，没有人类的主观因素；虽然加州伯克利大学/斯坦福大学的相关研究表明（见延伸阅读），
   自动化测评具有与人类评估的高度一致性（相关系数0.8-0.9），但进一步的分析还可以包括人类对模型的评估；
2. 评估的能力主要是基于SuperCLUE的十大基础能力，即使具有较高的代表性，但并不能保证覆盖了所有能力的评估。
3. 当前各个大模型厂商在快速迭代中，虽然我们报告的数字是最新的（7月中旬），但各个厂商的快速迭代可能会导致后续相对表现的进一步变化。
4. 在本文中，我们没有测试一些其他但有用的维度。比如，我们没有测试模型的性能问题（速度），也还没有测试模型的支持的有效的输入长度。后续可能会进行专门的测试。

## 延伸阅读
1. <a href='https://arxiv.org/abs/2307.15020'>SuperCLUE</a>: A Comprehensive Chinese Large Language Model Benchmark，
2. <a href='https://www.cluebenchmarks.com/superclue_open.html'>SuperCLUE-OPEN基准：中文通用大模型开放式与多轮测评基准（7月）</a> 
3. LMSYS文章：Chatbot Arena Leaderboard Week 8: Introducing MT-Bench and Vicuna-33B
4. 相关项目：Alpaca_Eval: A validated automatic evaluator for instruction-following language models

## 讨论与交流群

SuperCLUE榜单大模型评测申请：https://wj.qq.com/s2/12305633/a73d/

模型内测需求收集：https://wj.qq.com/s2/12307825/2ae0/

<p float="left">   
  <img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/superclue_llama2.jpeg"  width="30%" height="30%"></img>
  <img src="https://github.com/CLUEbenchmark/SuperCLUE/blob/main/resources/brightmart_s.jpeg"  width="30%" height="30%"></img>
</p> 

## 引用

如果使用本项目的，请引用本项目。

    @misc{SuperCLUE,
      author = {Liang Xu, Anqi Li, Lei Zhu, Hang Xue, Changtai Zhu, Kangkang Zhao, Haonan He, Xuanwei Zhang, Qiyue Kang, Zhenzhong Lan},
      title = {SuperCLUE: A Comprehensive Chinese Large Language Model Benchmark},
      year = {2023},
      publisher = {arxiv},
      howpublished = {\url{https://arxiv.org/abs/2307.15020}},
    }
