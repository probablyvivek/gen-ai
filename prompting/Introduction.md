### 1. **Prompt Tuning Parameters**

1. **Temperature**  
   - Controls **randomness** in token selection.  
   - **Low** = more **deterministic**, factual.  
   - **High** = more **creative**, diverse output.

2. **Top P (Nucleus Sampling)**  
   - Chooses from the top tokens adding up to `p` probability mass.  
   - **Low Top P** = confident, focused responses.  
   - **High Top P** = diverse, varied responses.  
   - *Tweak either Temperature **or** Top P, not both.*

3. **Max Length**  
   - Sets the **maximum number of tokens** in output.  
   - Helps control **response size** and **cost**.

4. **Stop Sequences**  
   - Predefined strings that **terminate generation**.  
   - Useful for structuring output (e.g., limit list items).

5. **Frequency Penalty**  
   - Penalizes tokens based on how **often** they’ve appeared.  
   - Helps **reduce word repetition**.

6. **Presence Penalty**  
   - Penalizes **whether** a token appeared, regardless of how many times.  
   - Encourages **novelty** and avoids **repeated ideas**.  
   - *Tweak either Frequency **or** Presence Penalty, not both.*

---

### 2. **Basics of Prompting**

#### **What is Prompting?**
Prompting is the art of giving instructions to a language model to get desired outputs. The prompt can include:
- **Instructions or questions**
- **Context**
- **Examples**

The more relevant and well-structured the input, the better the output quality.



#### **Basic Prompt Example**
**Prompt:**  
`The sky is`  
**Output:**  
`blue.`  

This shows how a model continues from a given phrase. However, results may vary unless clearer instructions are given.



#### **Improved Prompt**
**Prompt:**  
`Complete the sentence: The sky is`  
**Output:**  
`blue during the day and dark at night.`  

By giving a clearer instruction, you guide the model more effectively.



#### **Prompt Roles in Chat Models**
When using OpenAI chat models (e.g., GPT-3.5-turbo), prompts can include:
- **System**: Sets the tone/behavior (optional)
- **User**: Main instructions or questions
- **Assistant**: Example responses (optional for few-shot learning)



#### **Prompt Formats**
- **Instruction-based**:  
  `Summarize the following article.`
  
- **Question-based (QA Format)**:  
  `Q: What is prompt engineering?`  
  `A: Prompt engineering is...`



#### **Zero-Shot Prompting**
Asks the model to complete a task with **no prior examples**.  
Example:  
`What is prompt engineering?`



#### **Few-Shot Prompting**
Includes **multiple examples** of input-output pairs to guide the model.  
Example:  
```
This is awesome! // Positive  
This is bad! // Negative  
Wow that movie was rad! // Positive  
What a horrible show! //
```
**Output:**  
`Negative`

This is especially useful for classification, sentiment analysis, or custom logic tasks.

---

### 3. **Prompt Elements**

A well-crafted prompt may include four key elements:

**Instruction** – What task the model should perform.
Example: “Classify the text into neutral, negative, or positive.”

**Context** – Additional information to guide or steer the model.
Example: Previous examples of classifications.

**Input Data** – The actual question or text to analyze.
Example: “Text: I think the food was okay.”

**Output Indicator** – Specifies the expected format or type of output.
Example: “Sentiment:”

Not all four elements are required every time — it depends on the use case. The more clarity and structure you provide, the better the output tends to be.

---

### 4. **General Tips for Prompt Design**

#### **Start Simple and Iterate**
- Begin with a **basic prompt** and gradually refine it.
- Prompt engineering is **iterative**—experiment with format, detail, and structure.
- Break complex tasks into **smaller subtasks**.


#### **Effective Instructions**
- Use **clear command verbs** like: `Classify`, `Summarize`, `Translate`, `Extract`, etc.
- Place the instruction at the **start** of the prompt.
- Use **separators** (like `###`) to organize instruction, context, and input.

**Example:**
```
### Instruction ###
Translate the text below to Spanish:
Text: "hello!"
```

#### **Be Specific**
- The more **descriptive and precise**, the better the model understands the task.
- Provide **desired format/output examples** when necessary.
- Avoid **overloading** the prompt with irrelevant details.

**Example:**
```
Extract the name of places from the text.  
Format: Place: <comma-separated list>  
Input: “...at the Champalimaud Centre for the Unknown in Lisbon.”  
Output: Place: Champalimaud Centre for the Unknown, Lisbon
```

#### **Avoid Impreciseness**
- Don’t be vague like: “Keep it short and not too descriptive.”
- Instead, be specific: “Use 2–3 sentences to explain the concept to a high school student.”


#### **Avoid Negative Instructions**
- Rather than saying **what *not* to do**, say **what to do**.
- Positive, actionable guidance leads to more reliable responses.

**Poor Prompt:**
```
Do NOT ask for interests or personal information.
```

**Better Prompt:**
```
Recommend a movie from top trending titles without asking for user preferences. If no match, respond: "Sorry, couldn't find a movie to recommend today."
```

---
