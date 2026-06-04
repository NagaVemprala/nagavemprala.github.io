```markdown
# LLM Orchestration with LangChain

[← Back to Portfolio](index.html#works)

LangChain is a powerful open-source framework designed to simplify the construction of applications powered by Large Language Models (LLMs). By providing unified abstractions for components like prompt templates, memory, and model initializers, it enables developers to rapidly build context-aware, reasoning applications. Below are standard modern implementations for initializing underlying models and setting up autonomous tool-calling agents.

---

### 1. Using `init_chat_model` with OpenAI 5.5 Nano

The standard modern method to initialize a language model uses `init_chat_model`. This structural wrapper handles provider-agnostic initialization, allowing you to quickly swap models at runtime via standard application configuration.

```python
from langchain.chat_models import init_chat_model
from langchain_core.messages import HumanMessage

# 1. Initialize the chat model using the standard unified interface
model = init_chat_model(
    model="openai:gpt-5.5-nano",
    temperature=0.2,
    max_tokens=1000
)

# 2. Invoke the model directly using a message list
messages = [
    HumanMessage(content="Explain the operational advantage of an optimized RAG system.")
]

response = model.invoke(messages)
print(response.content)

```

---

### 2. Building an Agent via `create_agent`

Agents leverage an LLM as a core execution engine to determine an analytical plan and select external tools dynamically. The `create_agent` harness wraps the model with runtime middleware, tools, and instructions to process multi-turn workflows.

```python
from langchain.agents import create_agent
from langchain_core.tools import tool

# 1. Define custom analytical tools for the agent harness
@tool
def calculate_safety_stock(lead_time_days: int, demand_std_dev: float) -> float:
    """Calculates safety stock level required given standard deviation and lead time."""
    import math
    z_score = 1.65 # 95% service level standard
    return round(z_score * demand_std_dev * math.sqrt(lead_time_days), 2)

tools = [calculate_safety_stock]

# 2. Construct the agent with its foundational model, system behavior, and tools
agent = create_agent(
    model="openai:gpt-5.5-nano",
    tools=tools,
    system_prompt="You are an operations intelligence assistant. Use your tools to evaluate metric inputs."
)

# 3. Invoke the agent execution path with a target inquiry
input_state = {
    "messages": ["Calculate our safety stock if lead time is 9 days and demand standard deviation is 15 units."]
}

result = agent.invoke(input_state)
print(result["messages"][-1].content)

```

```

### Key Enhancements for GitHub Pages:
* **Syntax Highlighting:** Converted raw `<pre><code>` structures with custom internal styling classes (`keyword`, `string`, etc.) into formal native Markdown code blocks labeled with ` ```python `. This lets GitHub handle the syntax theme coloring natively.
* **Semantic Headers:** Remapped standard styling titles (e.g., `<h1 style="font-size: 50px">`) into semantic Markdown headings (`#` and `###`) so that auto-generated navigation trees parse the page correctly.
* **Clean Spacing:** Hand-coded styling spaces and margins have been replaced by standard clean horizontal rules (`---`) to keep the documentation professional and highly legible.

```