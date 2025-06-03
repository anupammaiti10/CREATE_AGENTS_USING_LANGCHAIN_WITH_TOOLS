# CREATE_AGENTS_USING_LANGCHAIN_WITH_TOOLS

This repository demonstrates how to create intelligent agents using [LangChain](https://github.com/hwchase17/langchain) and integrate them with custom tools for enhanced functionality.

## Overview

**LangChain** is a powerful framework for building applications powered by large language models (LLMs). In this project, we focus on building agents—autonomous programs that can reason, plan, and interact with various tools to solve complex tasks.

The agents in this repo can:
- Interpret user queries using LLMs
- Select and call relevant tools (e.g., search engines, calculators, APIs)
- Return coherent, actionable results

## Features

- **Modular Agent Design**: Build agents with plug-and-play tools
- **Tool Integration**: Easily add custom or external tools for the agent
- **Chain of Thought**: Agents reason step-by-step to achieve goals
- **Extensibility**: Add new tools or modify agent logic as needed

## Example Use Cases

- **Question Answering**: The agent can search documentation or external sources
- **Data Processing**: Use tools to manipulate, analyze, and summarize data
- **Automation**: Automate workflows by connecting to APIs or scripts

## How It Works

1. **Initialize LangChain**: Set up the language model and agent framework.
2. **Define Tools**: Implement or import tools with standard interfaces.
3. **Configure Agent**: Combine the LLM and tools into an agent with a reasoning strategy.
4. **Interact**: Send queries and receive intelligent multi-step responses.

## Getting Started

### Prerequisites

- Python 3.8+
- Install dependencies:

```bash
pip install langchain openai  # Add other requirements as needed
```

### Example Usage

```python
from langchain_openai import ChatOpenAI
model=ChatOpenAI(model="openai/o4-mini",base_url="https://openrouter.ai/api/v1", temperature=0.1, max_tokens=1500)
# We can first choose the prompt we want to use to guide the agent.

from langchain import hub
# Get the prompt to use - you can modify this!
prompt = hub.pull("hwchase17/openai-functions-agent")
prompt.messages

from langchain_core.prompts import ChatPromptTemplate
prompts=ChatPromptTemplate.from_messages(
   [ ("system", "You are a helpful assistant. Use tools when needed. You habe to be given query based on the query you have to be search most relevent information from the tools you have been given. You can use the tools Tavily Search, Wikipedia and LangSmith Search to answer the questions asked by the user. If you are not sure about the answer, you can use the tools to search for information."),
    ("user", "{input}"),
    ("assistant", "{agent_scratchpad}"),
    ]
)

# Run the agent
response = agent.run("What is the weather in New York?")
print(response)
```

## Folder Structure

```
.
├── agent.py           # Main agent implementation
├── README.md
└requirements.txt
```

## Contributing

Contributions are welcome! Please submit a pull request or open an issue.

## License

This project is licensed under the MIT License.

---

Feel free to modify the content to better describe your specific agents, tools, and use cases! If you want a more detailed example or help with specific sections, let me know.
