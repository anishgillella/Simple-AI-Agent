# Simple-AI-Agent

A lightweight, customizable AI agent implementation using LangChain and Hugging Face transformers. This project provides a flexible framework for building AI agents that can distinguish between information requests and actionable tasks, making it suitable for both question-answering and task execution scenarios.

## Features

- Custom AI agent implementation using LangChain's framework
- Automatic task/query classification
- Extensible tool system for adding new capabilities
- Structured response format for consistent outputs
- GPU acceleration support with automatic device selection
- Memory-efficient operation with proper cleanup

## Prerequisites

- Python 3.8+
- PyTorch
- Hugging Face account and API token
- Required Python packages (see Installation section)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/anishgillella/Simple-AI-Agent.git
cd Simple-AI-Agent
```

2. Install required packages:
```bash
pip install torch transformers langchain
```

3. Set up your Hugging Face credentials:
```bash
export HUGGING_FACE_HUB_TOKEN="your_token_here"
```

## Usage

1. Import and initialize the agent:
```python
from agent import setup_model, CustomAgent
llm = setup_model()
```

2. Create tools and initialize the agent executor:
```python
tools = [
    Tool(name="GetAnswer", func=get_answer, description="For general questions"),
    Tool(name="PerformAction", func=perform_action, description="For actionable tasks")
]

agent = CustomAgent(llm=llm, tools=tools)
agent_executor = AgentExecutor.from_agent_and_tools(
    agent=agent,
    tools=tools,
    verbose=True
)
```

3. Process queries:
```python
response = agent_executor.invoke({"input": "your query here"})
print(response["output"])
```

## Architecture

The project consists of two main components:

### CustomAgent
- Inherits from LangChain's `BaseSingleActionAgent`
- Determines whether queries require information or action
- Manages tool selection and execution

### CustomHuggingFaceLLM
- Wraps Hugging Face model pipeline
- Provides structured query processing
- Handles response formatting and validation

## Response Format

The agent provides responses in the following structure:
```
Response: [Answer to the query]
Category: [Information Request/Actionable Task/Clarification Needed]
Action Taken: [Description of action or None]
```

## Customization

### Changing the Model
Modify the `model_name` in `setup_model()` to use different Hugging Face models:
```python
model_name = "your-preferred-model"
```

### Adding New Tools
Create new tool functions and add them to the tools list:
```python
def new_tool_function(query: str) -> str:
    # Tool implementation
    return result

tools.append(Tool(
    name="NewTool",
    func=new_tool_function,
    description="Description of the new tool"
))
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Acknowledgments

- Built with [LangChain](https://github.com/hwchase17/langchain)
- Powered by [Hugging Face Transformers](https://github.com/huggingface/transformers)
- Inspired by the open-source AI community

## Contact

Anish Gillella - [@anishgillella](https://github.com/anishgillella)

Project Link: [https://github.com/anishgillella/Simple-AI-Agent](https://github.com/anishgillella/Simple-AI-Agent)
