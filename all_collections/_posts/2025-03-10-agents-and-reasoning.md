---
layout: post
title: "AI Agents and Reasoning: Thoughts and Insights"
date: 2025-03-19
categories: ["llm", "agents", "llm-reasoning", "ai"]
---

This blog shares insights and discussions on AI agents and reasoning based on conversations with colleagues and friends.

## AI Progress in 2025

AI progress this year is expected to be steady, focusing on:
- Improvements in inference optimization
- Refinement of reinforcement learning techniques
- Expansion of coding agents - especially since there’s plenty of wide data and the ability to execute code for intermediate results, like in math-related tasks

While these incremental improvements may seem like small upgrades, collectively, they could lead to a significant impact.

## Agents

### Definition
An agent is a system that perceives and interacts with the world using LLMs and tools/APIs.

### Example
A code-generating LLM becomes an agent when it can browse the web, use a terminal, and generate code simultaneously.

### Multi-Agent Systems
These involve multiple models collaborating to handle complex tasks.



## Computer Use from big Labs

Recent AI demonstrations provide insights into how AI agents might integrate into our systems:
- **Anthropic’s demo:** Ran within an OS container on a virtualized environment.
- **OpenAI’s demo:** Used a cloud-based browser with a few showcased applications.

In the future, eventually, AI agents will integrate seamlessly into existing systems so much so that we will not even notice them. It is similar to how neural networks are now embedded in everything from smartphone cameras to DSLRs and security systems.

## Challenges

### 1. Training Data
- The biggest is training. A model like this would need access to thousands of screenshots from various desktop, mobile, and web applications, along with handling dynamic UI elements.
- However, it would not need deep OS-level API interactions to function like a human. Instead, it would require a high-level understanding of user interfaces and basic interactions via keyboard and mouse.
- Specialization would come later, similar to how a person learns general UI interactions before mastering specific tools like Uber or some CRM app.

### 2. Generalization
- How generalizable these systems will be across different websites and apps?
- Widespread usability doesn’t have to happen all at once, like we don't rely on a single web app for all our needs; instead, we use a web browser that allows different servers and clients to communicate.
- AI agents will likely follow a similar trajectory. With emerging test-time scaling laws, there is little reason to doubt the potential of these systems.



## Reasoning in LLMs

### CoT
LLMs use Chain-of-Thought (CoT) to break down problems step by step.
 
This generates long reasoning sequences, making it look like they’re thinking. Sometimes the final answers could be from their stored knowledge instead of actually reasoning through a problem.
 
The existing models that score and critique responses (Reward Models & Critic Models) haven't really been tested properly to see how well they catch mistakes in these long reasoning chains.

### Key Issues (from Alibaba's DeltaBench Study) - [paper](https://arxiv.org/pdf/2502.19361)
1. **High Error Rates:** Models frequently make fundamental mistakes (math, logic, etc.).
2. **Critic Models Struggle:** Even top models (e.g., GPT-4-turbo-128k) only catch 40.8% of errors.
3. **Poor Self-Correction:** 67.8% of reflections don’t fix mistakes.
4. **Redundant Reasoning:** 27% of reasoning steps are unnecessary.
5. **Longer CoT, Worse Performance:** More reasoning steps lead to higher error rates.

### Takeaways
- LLMs aren't great at catching their own mistakes – They’re better at pointing out issues in others' responses than their own.
- Specialized "o1-like" models aren’t special – Models designed for long reasoning (like DeepSeek-R1) don’t do any better at error detection than regular models.

---
<br>
<br>

Thoughts from [Designing LLM Agents](https://vintagedata.org/blog/posts/designing-llm-agents)

The term agent is widely used in Reinforcement Learning, where agents are always interacting with their environment by making decisions or taking actions.
 
If LLM agents are trained using reinforcement learning (RL), as discussed in the blog, we have several challenges.

### Challenges
 
1. **Limited Data Availability:** Unlike math datasets (FineMath), search and action sequences are scarce in open datasets like Hugging Face.
 
2. **Monopoly on Data:** Major tech companies such as Google, OpenAI, and Anthropic hold a monopoly on key training data (search logs, user interactions).
 
3. **Simulation Based Training as an Alternative:** Instead of real web data, RL agents can be trained on synthetic browsing environments to mimic web search.

---
<br>

Here’s how I’m thinking about things right now:

### 1. Stability in LLM Reasoning
- Current reasoning still feels unstable and requires further research.

### 2. Context Window or LLM Memory
- This will be the key for reasoning, since a longer context window allows better multi-step reasoning, essential for handling complex tasks.

### 3. Breaking Down Complex Tasks
Instead of relying on a single, massive prompt, an agent can break tasks into smaller, more manageable steps.

#### Example: Travel Planning Chatbot
Imagine a chatbot assisting with travel planning. Instead of trying to fit all travel options, user preferences, and booking information into a single context window, an RL trained agent could:

- Ask clarifying questions to understand user needs.
- Query a travel database to retrieve relevant options.
- Present options to the user and gather feedback.
- Iteratively refine its search and recommendations based on user responses.
- Maintain state of the planning (date, destination, budget etc) across multiple turns.


## Conclusion

The development of AI agents and reasoning mechanisms is ongoing. While challenges remain, incremental improvements in reinforcement learning, training data, and reasoning capabilities will shape the future of AI-driven agents.
