# 底层原理

[返回主页](../README.md) | [**ChatGPT 简介**](ChatGPT-Introduction.md) | [**主要功能**](ChatGPT-Key%20Features.md) | [**底层原理**](ChatGPT-Underlying%20Principles.md) | [**基本操作**](ChatGPT-Basic%20Operations.md) | [**模型参数调整**](ChatGPT-Model%20Parameter%20Adjustment.md) | [**创建 GPTs**](ChatGPT-Creating%20GPTs.md) | [**插件**](ChatGPT-Plugins.md) | [**API 调用**](ChatGPT-API%20Calls.md) | [**ChatGPT 与其他软件的集成**](ChatGPT%20+%20Other%20Software.md) | [**提示词工程**](ChatGPT-Prompt%20Engineering.md) | [**示例**](ChatGPT-Examples.md) | [**常见问题解答**](ChatGPT-FAQ%20(Frequently%20Asked%20Questions).md)

首先需要解释，ChatGPT从根本上始终要做的是，针对它得到的任何文本产生“合理的延续”。这里所说的“合理”是指，“人们在看到诸如数十亿个网页上的内容后，可能期待别人会这样写”。

假设我们手里的文本是 **“The best thing about AI is its ability to”**。
想象一下浏览人类编写的数十亿页文本，
找到该文本的所有实例，
然后看看接下来出现的是什么词，
以及这些词出现的概率是多少。
ChatGPT 实际上做了类似的事情，
只不过它不是查看字面上的文本，
而是寻找在某种程度上“意义匹配”的事物。
最终的结果是，
它会列出随后可能出现的词及其出现的“概率”(按“概率”从高到低排列)。

The best thing about AI is its ability to

|下一个词|概率|
|-|-|
|learn|4.5%|
|predict|3.5%|
|make|3.2%|
|understand|3.1%|
|do|2.9%|

值得注意的是，
当 ChatGPT 做一些事情，
比如写一篇文章时，
它实质上只是在一遍又一遍地询问“根据目前的文本，下一个词应该是什么”，
并且每次都添加一个词。
**更准确地说，它是每次都添加一个“标记”(token)，而标记可能只是词的一部分。这就是它有时可以“造词”的原因。**

```
token 是一种方便的语言单位，既可以是整个词，也可以只是像 pre、ing 或 ized 这样的片段。
使用 token 可以使 ChatGPT 更容易处理罕见词复合词和非英语词，并且会发明新单词 (不论结果好坏)。
```
