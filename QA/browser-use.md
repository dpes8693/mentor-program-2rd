# 使用內部ollama模型 免費

base_url 群組提供

1.先把環境能跑起來
2.安裝Ollama套件
pip install langchain_ollama

```python
#by Gemini
from langchain_ollama import ChatOllama
from browser_use import Agent
from dotenv import load_dotenv
load_dotenv()

import asyncio

# Initialize the model with the new domain and model
llm=ChatOllama(base_url="https://example.com", model="qwen3:4b", num_ctx=32000)

async def main():
    agent = Agent(
        task=(
            '1. Go to https://www.reddit.com/r/LocalLLaMA'
            "2. Search for 'browser use' in the search bar"
            '3. Click search'
            '4. Call done'
        ),
        llm=llm,
        max_actions_per_step=1,
        tool_calling_method="json_schema",
        max_failures=6,
        use_vision=False
    )
    result = await agent.run()
    print(result)

asyncio.run(main())
```

===

## BrowserUse
<https://docs.browser-use.com/quickstart>

## 其他參考文件
<https://gist.github.com/hoyin258/581a03fc8ea347f6ec59102fd0ce406c>
<https://python.langchain.com/docs/integrations/chat/ollama/#installation>

## 模型上下文有限制
<https://g.co/gemini/share/87e0c5f46c9e>