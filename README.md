# langchain-openrouter

[![PyPI version](https://badge.fury.io/py/langchain-openrouter.svg)](https://badge.fury.io/py/langchain-openrouter)
[![Python versions](https://img.shields.io/pypi/pyversions/langchain-openrouter.svg)](https://pypi.org/project/langchain-openrouter/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Overview

This repo is a fork of https://github.com/StanMathers/langchain-openrouter. The main difference is addition of this README file

### NB: if you have OpenAI API keys added to PATH, this library and its .env setting will not prevent the routing of API calls to OpenAI rather than Openrouter. LangchainBase defaults to OpenAI and GPT4 and there is no simple change for novice users.

This package provides an integration between OpenRouter and LangChain. It allows you to easily use OpenRouter large language models (LLMs) within your LangChain applications.

## Installation

```bash
pip install langchain-openrouter
```

## Setup

Before using this package, you need to have an OpenRouter account and generate an API key. You can find instructions on how to do this in the OpenRouter documentation: [https://openrouter.ai/docs](https://openrouter.ai/docs)


### Using Dotenv

Store your API key in a `.env` file and use the `dotenv` library to load it into your environment.

First, install the `dotenv` library:

```bash
pip install python-dotenv
```

Then, create a `.env` file in the same directory as your script and add your API key:

```
OPENROUTER_API_KEY="your_api_key"
```

Finally, load the environment variables from the `.env` file in your script:

```python
import os
from langchain_openrouter import OpenRouterLLM
from dotenv import load_dotenv

# Load environment variables from .env file
load_dotenv()

# Initialize the OpenRouter LLM
llm = OpenRouterLLM(
    api_key=os.getenv("OPENROUTER_API_KEY"), 
    llm_type="gpt-4o-mini-2024-07-18", 
    model="openai/gpt-4o-mini-2024-07-18"
)

# ... rest of your code ...
```

This approach is generally considered more secure than hardcoding your API key directly in your script or using environment variables, especially when sharing your code publicly.

## Usage

Here's a simple example of how to use the OpenRouter LLM with LangChain:

```python
from langchain_openrouter import OpenRouterLLM

# Initialize the OpenRouter LLM
llm = OpenRouterLLM(
    api_key="your_api_key", 
    llm_type="gpt-4o-mini-2024-07-18", 
    model="openai/gpt-4o-mini-2024-07-18"
)

# Use the LLM to generate text
response = llm("Say: `Hello World!`")

# Print the response
print(response)
```

**Note:** Before using any LLM type or model, please refer to the OpenRouter documentation for valid options:

- **LLM types:** [https://openrouter.ai/docs#models](https://openrouter.ai/docs#models)
- **LLM models:** [https://openrouter.ai/docs#models](https://openrouter.ai/docs#models)
- **LLM parameters:** [https://openrouter.ai/docs#llm-parameters](https://openrouter.ai/docs#llm-parameters)
