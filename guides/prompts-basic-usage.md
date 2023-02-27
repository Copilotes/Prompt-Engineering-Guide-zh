# 基础提示

在前一篇指南中，我们介绍了并举了一个基本的提示示例。

在这篇指南中，我们将提供更多使用提示的示例，并介绍对于更高级指南非常重要的关键概念。

通常，学习概念的最好方法是通过示例运行。下面我们列举了一些示例，说明如何使用精心设计的提示来执行各种有趣和不同的任务。

Topics:
- [Text Summarization](#text-summarization)
- [Information Extraction](#information-extraction)
- [Question Answering](#question-answering)
- [Text Classification](#text-classification)
- [Conversation](#conversation)
- [Code Generation](#code-generation)
- [Reasoning](#reasoning)

---

## 文本摘要
自然语言生成中的标准任务之一是文本摘要。文本摘要可以包括许多不同的风格和领域。事实上，语言模型最有前途的应用之一就是能够将文章和概念汇总成快速且易于阅读的摘要。让我们尝试使用提示进行一个基本的文本摘要任务。

假设我想了解抗生素，我可以尝试一个像这样的提示：

*Prompt:*
```
解释抗生素

A:
```

*Output:*
```
抗生素是一类用于治疗细菌感染的药物。细菌感染可以导致各种疾病，例如肺炎、中耳炎、膀胱炎和皮肤感染等。抗生素通过抑制细菌的生长和繁殖来治疗这些感染。

抗生素可以分为多个类型，包括青霉素、头孢菌素、大环内酯类和氨基糖苷类等。每种类型的抗生素都有不同的作用方式和适应症。

值得注意的是，抗生素只对细菌感染有效，对病毒感染无效。过度使用抗生素会导致耐药性，使得细菌逐渐对抗生素产生抵抗力，从而导致抗生素治疗失效。因此，正确使用抗生素非常重要。在使用抗生素之前，应该首先确定感染的类型，并遵循医生的建议使用适当的药物和剂量。
```

The "A:"是一种明确的提示格式，用于问答。我在这里使用它是为了告诉模型后面还有预期的信息。在这个例子中，不清楚这与不使用它相比有何用处，但我们将在以后的例子中讨论这个问题。现在，让我们假设这是过多的信息，我们想要进一步摘要。实际上，我们可以指示模型将其总结为一句话，如下所示：

*Prompt:*
```
抗生素是一种用于治疗细菌感染的药物。它们通过杀死细菌或阻止其繁殖，使身体免疫系统能够抵抗感染。抗生素通常以口服药片、胶囊或液体溶液的形式服用，或者有时通过静脉注射给药。它们对病毒感染无效，不合理使用会导致抗生素耐药性。

用一句话解释上述内容:
```

*Output:*
```
抗生素是用于治疗细菌感染的药物，通过杀死细菌或阻止其繁殖，但对病毒无效，过度使用会导致抗生素耐药性。
```

不必过分关注上面输出的准确性，这是我们将在后面的指南中讨论的内容，该模型试图用一句话总结段落。你可以通过尝试不同的方式来获得更好的结果，但我们将在后面的章节中介绍。随意暂停并尝试以查看是否能得到更好的结果。

---
## 信息提取
虽然语言模型被训练用于执行自然语言生成和相关任务，但它也非常擅长执行分类和一系列其他自然语言处理（NLP）任务。

以下是从给定段落中提取信息的提示的示例。

*Prompt:*
```
研究论文中的作者贡献声明和致谢应清楚明确地说明作者是否以及在何种程度上在撰写和分析稿件时使用了像ChatGPT这样的人工智能技术，并应指明使用了哪些大型语言模型（LLMs）。这将提醒编辑和审稿人更仔细地审查稿件，以防潜在的偏见、不准确性和不当的来源引用。同样，科学期刊在选择提交的稿件时，也应透明地公布其使用LLMs的情况。

请提及上文提到的基于大型语言模型的产品:
```

*Output:*
```
上文提到的基于大型语言模型的产品是ChatGPT。
```

我们可以采取许多方法来改进上面的结果，但这已经非常有用了。

现在显然可以看出，您可以通过简单地指示模型要做什么来要求模型执行不同的任务。这是一种强大的能力，已经被人工智能产品开发者用于构建强大的产品和用户体验。


来源: [ChatGPT: five priorities for research](https://www.nature.com/articles/d41586-023-00288-7) 

---
## 问答

将模型训练成产生特定答案的最佳方法之一是改进提示的格式。如前所述，提示可以结合指令、上下文、输入和输出指示符来获得更好的结果。虽然并不是所有组成部分都是必需的，但随着您在指令上变得更加具体，结果也会更好，这是一种良好的实践。以下是一个更加结构化的提示的示例，展示了它的具体样式。

*Prompt:*
```
基于以下上下文回答问题。回答要简短明了。如果不确定答案，请回答“不确定答案”。

上下文：Teplizumab可追溯到一家名为Ortho Pharmaceutical的新泽西州制药公司。在那里，科学家们生成了一种早期版本的抗体，被称为OKT3。分子最初是从老鼠中提取的，能够结合T细胞表面并限制它们的杀伤细胞潜力。1986年，它被批准用于帮助预防肾移植后的器官排斥，使其成为第一种允许人类使用的治疗性抗体。



Answer:
```
问题：OKT3最初是从哪里提取的？

*Output:*
```
回答：OKT3最初是从老鼠中提取的。
```

获得的上下文 from [Nature](https://www.nature.com/articles/d41586-023-00400-x).

---

## 文本分类
到目前为止，我们使用了简单的指令来执行任务。作为提示工程师，您需要提供更好的指令来提高工作效率。但这还不是全部！您还会发现，在更困难的用例中，仅仅提供指令是不够的。这就需要您更多地考虑上下文和提示中可以使用的不同元素。您可以提供的其他元素包括输入数据或示例。

让我们尝试通过提供文本分类的示例来说明这一点。

*Prompt:*
```
请分类文本为中性、负面或积极。

Text:我认为食物还好. 
请分类文本为中性、负面或积极:
```

*Output:*
```
中性
```

我们给出了对文本进行分类的指令，模型的回应是'Neutral'，这是正确的。这里没有什么问题，但是假设我们真正需要的是模型以我们想要的确切格式返回标签。因此，我们不是要返回“Neutral”，而是要返回“neutral”。我们如何实现这一点呢？有不同的方法。在这里我们关注的是具体性，因此我们提供的提示信息越多，结果就越好。我们可以尝试提供示例以明确正确的行为。让我们再试一次：

*Prompt:*
```
请将文本分类为中性、负面或积极。

基于以下文本： "我认为假期还不错。"，请将文本分类为中性、负面或积极。

答案：中性

Text: 我认为食物还好
Sentiment:
```

*Output:*
```
中性
```

太好了！这次模型返回了我想要的特定标签“中性”。看来在提示中提供的示例帮助模型在输出中具体化了。为了强调为什么有时候具体性很重要，请查看以下示例并发现问题：

*Prompt:*
```
请将文本分类为中性、负面或积极。

我认为假期还不错
答案:
```

*Output:*
```
中性
```

这里的问题是什么？

---

## 会话
也许提示工程的一项更有趣的事情是告诉系统如何行动、它的意图和身份。当您正在构建会话系统时，这特别有用。

例如，让我们创建一个会话系统，它能够回答更多技术和科学问题。请注意，我们是通过指令明确地告诉它如何行动的。

*Prompt:*
```
以下是与一个AI研究助手的对话。助手的语气是技术性和科学性的。

人类：你好，你是谁？
AI：您好！我是一名AI研究助手。今天有什么需要我帮助您的吗？
人类：你能告诉我黑洞的形成吗？
AI:
```

*Output:*
```
当然可以！黑洞是时空中的一些区域，其中的引力非常强大，以至于任何东西，甚至是光，都无法从中逃脱。它们的形成是由于一个非常质量大的恒星死亡时，它的核心向内坍缩，形成了一个无限密度的奇点。奇点的强烈引力将其周围的所有物质和辐射吸引过来，形成了黑洞。
```

Our AI research assistant sounds a bit too technical, right? Okay, let's change this behavior and instruct the system to give more accessible answers. 

*Prompt:*
```
The following is a conversation with an AI research assistant. The assistant answers should be easy to understand even by primary school students.

Human: Hello, who are you?
AI: Greeting! I am an AI research assistant. How can I help you today?
Human: Can you tell me about the creation of black holes?
AI: 
```

*Output:*
```
Sure! Black holes are created when a very massive star runs out of fuel and collapses in on itself. The gravity of the star is so strong that nothing, not even light, can escape its pull. This creates a point in space-time with an intense gravitational force called a black hole.
```

I think we made some progress. You can continue improving it. I am sure if you add more examples you might get even better results. 

---

## Code Generation
One application where LLMs are quite effective at is code generation. Copilot is a great example of this. There is a vast number of code generation tasks you can perform with clever prompts. Let's look at a few examples below.

First, let's try a simple program that greets the user. 

*Prompt:*
```
/*
Ask the user for their name and say "Hello"
*/
```

*Output:*
```
let name = prompt("What is your name?");
console.log(`Hello, ${name}!`);
```

You can see that we didn't even need to specify language to use. 

Let's switch levels a bit. I want to show you how powerful LLMs can be with a little more effort on designing the prompts.

*Prompt:*
```
"""
Table departments, columns = [DepartmentId, DepartmentName]
Table students, columns = [DepartmentId, StudentId, StudentName]
Create a MySQL query for all students in the Computer Science Department
"""
```

*Output:*
```
SELECT StudentId, StudentName 
FROM students 
WHERE DepartmentId IN (SELECT DepartmentId FROM departments WHERE DepartmentName = 'Computer Science');
```

This is very impressive. In this case we provided data about the database schema and asked it to generate a valid MySQL query. 

---

## Reasoning
Perhaps one of the most difficult tasks for an LLM today is one that requires some form of reasoning. Reasoning is one the areas that I am most excited about due the types of complex applications that can emerge from LLMs. 

There have been some improvements on tasks involving mathematical capabilities. That said, it's important to note that current LLMs struggle to perform reasoning tasks so this require even more advanced prompt engineering techniques. We will cover these advanced techniques in the next guide. For now, we will cover a few basic examples to show arithmetic capabilities.

*Prompt:*
```
What is 9,000 * 9,000?
```

*Output:*
```
81,000,000
```

Let's try something more difficult. 

*Prompt:*
```
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1. 

A: 
```

*Output*
```
No, the odd numbers in this group add up to an odd number: 119.
```

That's incorrect! Let's try to improve this by improving the prompt.

*Prompt:*
```
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1. 

Solve by breaking the problem into steps. First, identify the odd numbers, add them, and indicate whether the result is odd or even. 
```

*Output:*
```
Odd numbers: 15, 5, 13, 7, 1
Sum: 41 
41 is an odd number.
```

Much better, right? By the way, I tried this a couple of times and the system sometime fails. If you provide a better instruction combined with examples, it might help get more accurate results.

We will continue to include more examples of common applications in this section of the guide.

In the upcoming guides, we will cover even more advanced prompt engineering concepts for improving performance on all these and more difficult tasks.

---

[Previous Section (Prompts Introduction)](./prompts-intro.md)

[Next Section (Advanced Prompting Techniques)](./prompts-advanced-usage.md)
