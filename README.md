# LLM Query Processing Agent

A Python-based Language Model agent that processes user queries using LangChain and LLaMA. This system categorizes queries, generates appropriate responses, and handles task-based actions.

## Features

- Query processing and categorization
- Automated response generation
- Task handling capability with todo list management
- Support for both GPU and CPU processing
- Structured response format with categories and reasoning

## Prerequisites

```bash
# Core dependencies
langchain
transformers
torch
huggingface_hub
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/anishgillella/Simple-AI-Agent.git
```

2. Create a virtual environment:
```bash
python -m venv env
source env/bin/activate  # On Windows use: env\Scripts\activate
```

3. Install required packages:
```bash
pip install langchain transformers torch huggingface_hub langchain-community
```

## Usage

The main script provides an interactive interface:

```python
python main.py
```

Enter queries when prompted. Type 'quit' or 'exit' to end the session.

Example interactions:
```
Enter your query: Create a todo list for my project
Response: I will create a new todo list for your project
Category: Actionable Task
Reason: The request involves creating a concrete item

Enter your query: What time is it?
Response: I need more context about your timezone
Category: Clarification Needed
Reason: Time information requires contextual details
```

## Code Structure

- `setup_model()`: Initializes LLaMA model and tokenizer
- `extract_response_parts()`: Processes model output into structured components
- `generate_action_statement()`: Creates completion statements for tasks
- `run_agent()`: Main processing pipeline for queries
- `SimpleActionTool`: Handles todo list management operations

## Response Categories

The system categorizes responses into three types:
1. Information Request
2. Actionable Task
3. Clarification Needed

## Error Handling

The system includes comprehensive error handling:
- Model initialization errors
- Processing pipeline failures
- File system operation errors
- Invalid query handling

## Limitations

- Requires access to LLaMA model
- English language input only
- Local file system access needed for todo list functionality
- No persistent storage of conversation history

## Contributing

1. Fork the repository
2. Create a new branch
3. Implement your changes
4. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Quick Start Example

```python
from main import run_agent

# Process a single query
result = run_agent("Create a todo list for my project")
print(f"Response: {result['response']}")
print(f"Category: {result['category']}")
print(f"Reason: {result['reason']}")
```

For more examples and detailed documentation, see the examples directory.
