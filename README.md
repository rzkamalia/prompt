# ChatGPT Prompt Engineering for Developers

This repository is note from watching video [DeepLearning.AI - ChatGPT Prompt Engineering for Developers](https://learn.deeplearning.ai/courses/chatgpt-prompt-eng/).


### Principal of Prompting
1. Write clear and spesific instructions.
2. Give the model time to think.

**1. Write clear and spesific instructions.**
+ **Use delimiters to clearly indicate distinct parts of the input.** Delimiter can be like: 
```
```, """, < >, :
```
+ **Ask for a structured output.** 
```
prompt = """
...

Provide them in JSON format with the following keys: A, B, C.
"""
```
+ **Ask the model to check whether conditions are satisfied.**
```
prompt = """
You will be provided with text bellow. 
If it contain a sequence of instruction, re-write those instruction in the following format:
Step 1 - ...
Step 2 - ...
...
Step N - ...
If the text does not contain a sequence of instuction, the simply write "No steps provided".

text = ...
"""
```
+ **Few-shot learning.** Give successful examples of completing tasks, then ask model to perform the task. 
```
prompt = """
Your task is to answer in a consistent style.
<student> : Teach me about mathematics.
<teacher> : Mathematics is an area of knowledge that includes the topics of numbers, formulas and related structures, shapes and the spaces in which they are contained, and quantities and their changes. 
<student> : Teach me about physics. 
"""
```

**2. Give the model time to think.**
+ **Specify the steps required to complete a task.**
```
prompt = """
Perform the following action:
1. Summarize the following text.
2. Translate the summary to Korea.
3. Output a JSON that contain the following keys: englist_text and korean_text.

Use the following format:
Summary : <summary>
Translate : <summary translation>
Output JSON : <JSON with english_text and korean_text>

text = ...
"""
```

### Prompt Development Guideline
1. Be clear and spesific.
2. Analyze why result does not give desired output.
3. Refine the idea and the prompt.
4. Repeat.

### Example 
+ **Prompt for Summarizing**
```
prompt = """
Your task is to generate summary of ...

Summarize the text below, and focusing on ...

text = ...
"""
```

+ **Prompt for Inferring Sentiment** \
If you only want the result directly in the form "negative" or "positive", then in the prompt you can add :
```
...

Give your answer as single word, either "negative" or "positive".
```

+ **Prompt for Inferring Emotion** 
```
prompt = """
Is the writer of the following review expressing anger?

review = ...
"""
```

+ **Prompt for Inferring Topic** 
```
prompt = """
Determine five topicsw that are discussed in the following text. 
Make each item one or two long.
Format your response as list of items separate by comma.

text = ...
"""
```

### Suggestion
If you want to make a good result, make sure there are the following content in your prompt.
```
prompt = """
You are a ... .
Your task is to ... .
Generate ... .
<write condition, if any>
Make sure to use ... <if any>.
Write in a <format output>.
"""
```
For example:
```
prompt = """
You are a customer service AI assistant.
Your task is to send an email reply to a valued customer.
Generate a reply to thank the customer for their review.
If the sentiment is positive or neutral, thank them for their review. If the sentiment is negative, apologize and suggest that they can reach out to customer service. 
Make sure to use specific details from the review.
Write in a concise and professional tone.

customer review: ...

review sentiment: ...
"""
```
