# AngelAgent
AI agent for the new era! Retrieval and generation are different!!

## Plan
1. 使用Transformer实现基于文本的任务分类；
2. 长文本切片为短文本，每个短文本对应一个原子任务，多个原子任务串起来形成一个任务链。

## Detail
1. 分类任务和任务链规划；
2. 分类任务决定可能动用哪些原子能力；
3. 任务链规划模型决定将哪些原子能力组合起来，并以什么顺序组合；
4. 需检验每个任务的输出和下一个任务的输入是否吻合，即入参检验，包括类型是否匹配以及值的范围合法性；
5. 如第4步不吻合，则进入重新规划环节（反思），基于分类信息和上一次失败的经验，重新规划；
6. 如第5步循环多次依然无法给出合理任务链，达到重试上限，记录到日志，返回不可实现；
7. 如生成合理任务链，则按序执行，返回处理结果。

## References
https://huggingface.co/docs/transformers/en/tasks/sequence_classification

## Q&A
Question:
I provide several atomic capabilities. Now there is a long text. And I want to split this long text into a chain of tasks supported by atomic capabilities. How to do it with transformer?
Answer:
To split a long text into a chain of tasks supported by atomic capabilities using a Transformer model, you would typically follow a process that involves understanding the text, identifying the tasks, and then breaking down those tasks into atomic capabilities. Here's a step-by-step approach to how you might do this:

1. **Text Understanding**:
   - Use a pre-trained Transformer model (like BERT, GPT, or T5) to understand the context and meaning of the long text. This model should be capable of comprehending the text at a level where it can identify different topics or intentions within the text.

2. **Task Identification**:
   - Apply a task identification mechanism to determine the distinct tasks within the text. This could be a rule-based system, a heuristic approach, or another machine learning model that classifies different segments of the text as different tasks.

3. **Atomic Capability Mapping**:
   - Once tasks are identified, map each task to the most suitable atomic capability. Atomic capabilities are the smallest units of work that can be performed independently. You would need to have a predefined set of atomic capabilities that are relevant to the tasks at hand.

4. **Chaining Tasks**:
   - After mapping tasks to atomic capabilities, you need to chain these tasks in a logical order. This could be based on dependencies between tasks or the sequence in which they were mentioned in the text.

5. **Model Fine-tuning (Optional)**:
   - If you have a specific Transformer model that is meant for task decomposition, you might need to fine-tune it on a dataset where tasks and their atomic capabilities are clearly labeled. This will help the model learn the patterns and relationships between complex tasks and their simpler components.

6. **Validation and Testing**:
   - Validate the output of the task decomposition process by checking if the split tasks and their corresponding atomic capabilities accurately reflect the original text's intent and content.

7. **Iterative Refinement**:
   - The process may require iterative refinement, especially in the initial stages. You might need to adjust your approach based on the accuracy and effectiveness of the task decomposition.

It's important to note that while Transformer models are powerful and can understand complex language patterns, they may not inherently understand the concept of atomic capabilities or task decomposition without proper training data. The success of this process will depend on the quality of the pre-trained model, the accuracy of the task identification mechanism, and the clarity of the atomic capabilities mapping.

If you're working with a domain-specific text, it might be beneficial to fine-tune your Transformer model on domain-specific data to improve its understanding of the tasks and atomic capabilities relevant to your application.
