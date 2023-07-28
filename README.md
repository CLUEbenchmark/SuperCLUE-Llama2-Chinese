# SuperCLUE-Llama2-Chinese
Llama2中文版开源模型全方位测评，基于SuperCLUE基准



## 概要
Facebook母公司Meta发布了开源可商用的大模型Llama2，该开源模型受到广泛关注。Llama2为初创企业和其他企业提供了一个强大的免费选择。新版本Llama2将训练数据量增加了 40%，它包括70亿、130亿和700亿参数量的多个版本，此外还有对应的聊天机器人调优版本Llama 2-Chat。最近国内外大厂包括微软、阿里云等也宣布支持Llama2。开源社区和大量机构、个人，也纷纷着手基于Llama2构建中文版本及其应用。

基于Llama2的中文版本的效果怎么样？当前开源版本做到什么程度了；与国内代表性模型相比，特别是开源模型（baichuan-13b, chatglm2-6b）的相对表现如何；在一些比较关注的能力上，如生成与创作、逻辑推理、代码生成，表现怎么样呢？

基于SuperCLUE开放式与多轮测评基准（OPEN），即针对开放式的问题并结合多轮对话能力的测试，我们首次对Llama2中文版模型进行了定量和定性评估。通过前者可以看到模型的相对其他模型的表现，以及十大能力维度上的表现；而后者从一些典型示例中看到模型的表现（包括相对成熟和不足的能力）。


<img src="https://github.com/CLUEbenchmark/Llama2-Chinese/blob/main/resources/img/llama2_chinese_v3.jpg"  width="90%" height="90%"></img>
