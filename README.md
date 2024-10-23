# Simple-AI-Agent

A lightweight, customizable AI agent using LangChain and Hugging Face transformers. It categorizes queries, executes tasks, and returns structured responses.

## Features

- Custom AI agent with LangChain
- Automatic query/task classification
- Extensible tool system
- GPU acceleration and efficient memory use

## Prerequisites

- Python 3.8+
- PyTorch
- Hugging Face account and API token

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/anishgillella/Simple-AI-Agent.git
    cd Simple-AI-Agent
    ```

2. Install packages:
    ```bash
    pip install torch transformers langchain langchain-community
    ```

3. Set up Hugging Face credentials:
    ```bash
    export HUGGING_FACE_HUB_TOKEN="your_token_here"
    ```

## Usage

1. Import and set up:
    ```python
    from simple_agent import setup_model, CustomAgent

    llm = setup_model()
    ```

2. Create tools and initialize the agent:
    ```python
    from langchain.agents import Tool, AgentExecutor

    tools = [Tool(name="GetAnswer", func=get_answer), Tool(name="PerformAction", func=perform_action)]
    agent = CustomAgent(llm=llm, tools=tools)
    agent_executor = AgentExecutor.from_agent_and_tools(agent=agent, tools=tools)
    ```

3. Process queries:
    ```python
    response = agent_executor.invoke({"input": "your query here"})
    print(response["output"])
    ```

## Response Format

```
Response: [Answer]
Category: [Information Request/Actionable Task/Clarification Needed]
Action Taken: [Description or None]
```

## Colab Notebook

Use the [Colab notebook](https://colab.research.google.com/drive/19EVWG6nMTp55OanSNHXOMBHEo9RLKk5h#scrollTo=vTdRdhxQKC_J) for quick execution.

## Contributing

1. Fork the repo, create a feature branch, and submit a Pull Request.

Project Link: [https://github.com/anishgillella/Simple-AI-Agent](https://github.com/anishgillella/Simple-AI-Agent)
