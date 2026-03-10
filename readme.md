# AI AGENTS FUNDAMENTALS

This notebook demonstrates about AI Agent fundamentals
- AI agent is build with the help of
- 1. Prompt
- 2. LLM
- 3. Tools

Firstly build tools which are needed in AI agent.Here take a example of maths tutor AI Agent.
## Tools
- Create tools for basic four arithmetic operations.
```python
from langchain_core.tools import tool
@tool
def add(a:int,b:int):
    """
     return addition of given numbers
     Args:
        a:first
        b:second
    """
    return a + b
add.invoke({"a":3,"b":4})
```
## Tools connected with LLM
- Now connect the tools with LLM

```python
from langchain.agents import create_agent
llm = ChatOpenAI(model="openai/gpt-4o", base_url="https://openrouter.ai/api/v1",max_tokens=1000)
agent = create_agent(model=llm,tools=[product,add],system_prompt='you are a maths teacher nad use tools for calculation')
ans = agent.invoke({"messages":[{"role":"user","content":"what is the product of 5 and 6?"}]})
ans["messages"][-1].content 
```
- `[-1]` used for the content of last processing step
- `[0]` similarly for question

## Setup

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Environment Configuration

Create a `.env` file in the project root with:

```env
OPENAI_API_KEY=your_api_key_here
```

### 3. Getting Your API Key

- Register at [Openai](https://openai.ai)
- Generate your API key
- Add it to your `.env` file

## File Structure

- `tools.ipynb` - Main notebook
- `.env` - Environment variables (local only, not in git)
- `.gitignore` - Git ignore rules
- `requirements.txt` - Python dependencies
