# MCP


## 基础介绍

MCP Server框架


AI Agent核心问题：
- Planing: 规划大模型行动 
- Action: 行动的基本流程
- Memory: 对话记忆
- Tools: 连接外部工具

MCP主要解决了统一外部工具的问题


## 核心内容
```yaml
mcp:
    server:
        fastmcp:
            FastMCP:
                @resource:
                @tool:
                run():
                    transport:
                        stdio:    
    ClientSession:
    StdioServerParameters:
openai:
    OpenAI:
        api_key:
        base_url:
        chat:
            completions:
                create():
                    choices:
                        message:
                            content:
```