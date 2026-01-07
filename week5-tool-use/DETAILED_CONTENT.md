# 🎓 MCP Learning Path - Nội Dung Chi Tiết

## 📋 Overview

Khóa học này hướng dẫn bạn từ **Function Calling cơ bản** → **MCP Server** → **Agentic Chatbot** với **LangGraph**

**Thời gian:** 8-10 hours  
**Yêu cầu:** Basic Python, hiểu biết LLM  
**Kết quả:** Có thể xây dựng production MCP systems

---

## 📚 Notebook 1: Lý Thuyết & Ví Dụ

### Phần 1: Function Calling Cơ Bản từ Scratch (Cells 1-20)

**Khái niệm:**
- Function calling là cách LLM gọi các tools/functions
- LLM phân tích user input → quyết định tool → thực thi → trả kết quả

**Cấu trúc Code:**
```
Tools (functions)
    ↓
Tool Registry (quản lý tools)
    ↓
Mock LLM (quyết định tool)
    ↓
Function Calling Loop (thực thi)
    ↓
Output formatting
```

**Ví dụ Thực Tế:**
```
User: "5 cộng 3 bằng bao nhiêu?"
↓
LLM: Nhận diện cần gọi "add" tool
↓
Call: add(a=5, b=3)
↓
Result: 8
↓
Response: "5 cộng 3 bằng 8"
```

**Code Examples:**
- ✅ `calculator()`: Cộng, trừ, nhân, chia
- ✅ `get_weather()`: Mock weather API
- ✅ `search_knowledge_base()`: Mock search engine
- ✅ `ToolRegistry`: Quản lý 3 tools trên

**Kiến Thức:**
- Hiểu flow: input → tool selection → execution → output
- Biết cách implement tool registry
- So sánh: manual vs OpenAI API

---

### Phần 2: Vấn Đề Thực Tế (Cells 21-30)

**Vấn Đề 1: Nhiều LLM, Nhiều Format**
```
OpenAI:   {type: "function", function: {...}}
Claude:   {name: "...", input_schema: {...}}
Gemini:   {function_declarations: [...]}
```
**Hậu quả:** Phải code riêng cho từng LLM

---

**Vấn Đề 2: Nhiều Tools, Khó Maintain**
```
System A: [calculator, weather, search]
System B: [calendar, email, database]
System C: [calculator, weather, calendar, email, database]
```
**Hậu quả:** Copy-paste, inconsistent, khó update

---

**Vấn Đề 3: Tight Coupling**
```
LLM cần biết chi tiết implement của tool
→ Thay đổi tool → phải update LLM code
→ Khó scale khi nhiều tool servers
```

---

**Vấn Đề 4: Không Có Giao Thức Chung**
```
Mỗi company tự implement → không interoperability
```

---

**Giải Pháp: MCP**
```
Giao thức chung (standard) → LLM không cần biết detail
                          → Tool servers hoàn toàn decoupled
                          → Dễ reuse, maintain, scale
```

---

### Phần 3: MCP là Gì? Kiến Trúc (Cells 31-50)

**Định Nghĩa:**
MCP = **Model Context Protocol** - giao thức standard từ Anthropic để kết nối LLM với external tools/resources

**Tương Tự:**
```
HTTP  → Web Browser kết nối Web Server
MCP   → LLM Client kết nối Tool Server
```

---

**Architecture (High Level):**
```
┌──────────────────┐       MCP Protocol (JSON-RPC)      ┌──────────────────┐
│ MCP Client       │ ────────────────────────────────── │ MCP Server       │
│ (LLM + Agent)    │                                    │ (Tools/Resources)│
└──────────────────┘                                    └──────────────────┘
```

---

**Message Flow:**
```
1. Client: Initialize Request → Server
2. Server: Initialize Response → Client
3. Client: ListTools Request → Server
4. Server: [tool1, tool2, ...] → Client
5. Client: CallTool(name, args) → Server
6. Server: result → Client
```

---

**MCP Server Capabilities:**
- **Tools**: Executable functions (like function calling)
- **Resources**: Read-only data (files, templates, docs)
- **Prompts**: Reusable prompt templates
- **Sampling**: Delegate inference to LLM

---

**So Sánh: Function Calling vs MCP**

| Aspect | Function Calling | MCP |
|--------|------------------|-----|
| Giao thức | Riêng cho từng LLM | Unified standard |
| Decoupling | Cao | Rất cao |
| Scalability | Khó | Dễ |
| Reusability | Thấp | Cao |
| Standardization | Không | Có (Anthropic) |

---

### Phần 4: Tạo MCP Server từ Scratch (Cells 51-80)

**MCP SDK Installation:**
```bash
pip install mcp
```

---

**Calculator Server Example:**
```python
from mcp.server import Server
from mcp.types import Tool, TextContent

server = Server("calculator-server")

@server.call_tool()
async def call_calculator(name: str, arguments: dict):
    if name == "add":
        return [TextContent(type="text", text=str(arguments["a"] + arguments["b"]))]
    ...

@server.list_tools()
async def list_tools():
    return [
        Tool(
            name="add",
            description="Cộng hai số",
            inputSchema={...}
        ),
        ...
    ]
```

---

**Key Components:**
- `Server(name)`: Tạo server instance
- `@server.call_tool()`: Handler cho tool execution
- `@server.list_tools()`: Handler cho tool discovery
- `Tool`: Schema của một tool
- `TextContent`: Return type cho tool result

---

**Weather Server (Advanced):**
```
Tools:
- get_weather(city) → weather info
- get_weather_forecast(city, days) → forecast
- list_cities() → available cities

Resources:
- weather://city/{city_name} → read-only data
```

---

### Phần 5: Kết Nối LLM với MCP Server (Cells 81-100)

**MCP Client:**
```python
class MCPClient:
    async def list_available_tools(self):
        # Gọi server.list_tools()
        pass
    
    async def call_tool(self, tool_name, **kwargs):
        # Gọi server.call_tool()
        pass
```

---

**Request-Response Flow:**
```
Client Request:
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/call",
  "params": {"name": "add", "arguments": {"a": 5, "b": 3}}
}

Server Response:
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {"content": [{"type": "text", "text": "8"}]}
}
```

---

### Phần 6: Sử Dụng MCP với LangChain (Cells 101-120)

**LangChain Integration:**
```python
from langchain_core.tools import StructuredTool

# Tạo tool từ MCP server
calculator_tool = StructuredTool(
    name="calculator",
    description="...",
    func=mcp_client.call_tool,
    args_schema={...}
)

# Sử dụng trong agent
agent = create_react_agent(llm, [calculator_tool, ...])
```

---

**Workflow:**
```
LangChain Agent
    ↓
LLM quyết định tool
    ↓
MCP Client (integrated)
    ↓
MCP Server
    ↓
Kết quả → Agent → Response
```

---

### Phần 7: Xây Dựng Agentic Chatbot với LangGraph (Cells 121-150)

**LangGraph Basics:**
```python
from langgraph.graph import StateGraph

# 1. Define State
class AgentState(TypedDict):
    messages: list
    tools_used: list

# 2. Create Graph
graph = StateGraph(AgentState)

# 3. Add Nodes
graph.add_node("agent", agent_node)
graph.add_node("tools", tool_node)
graph.add_node("end", end_node)

# 4. Add Edges
graph.add_edge("agent", "tools")
graph.add_edge("tools", "agent")
graph.add_edge("agent", "end")

# 5. Set Entry Point
graph.set_entry_point("agent")
graph.set_finish_point("end")

# 6. Compile
runnable = graph.compile()
```

---

**Agent Workflow:**
```
START
  ↓
Agent Node: LLM + tools schema
  ↓ (Decision: call tool?)
YES → Tool Node: execute tool(s)
        ↓ (More tools needed?)
        YES → back to Agent Node
        NO → to End Node
NO → End Node: final response
  ↓
OUTPUT
```

---

**Multi-turn Conversation:**
```
User Input 1
  ↓ (Agent calls tools)
  ↓ (Results added to state)
  ↓
User Input 2
  ↓ (Agent sees previous context + tools)
  ↓ (Can make smarter decisions)
  ...
```

---

## 📖 Notebook 2: Bài Tập Thực Hành

### Bài 1: Function Calling Cơ Bản (30-45 min)

**Mục tiêu:** Tạo function calling system đơn giản

**Tasks:**
1. Implement 3 tools: `add()`, `subtract()`, `get_length_of_string()`
2. Tạo `ToolRegistry` class
3. Đăng ký 3 tools vào registry
4. Implement `mock_llm_decision()` - quyết định tool
5. Implement `function_calling_loop()` - thực thi
6. Test với 3 test cases

**Expected Output:**
```
Input: "What is 10 plus 5?"
Output: "10 plus 5 equals 15"

Input: "20 minus 8?"
Output: "20 minus 8 equals 12"

Input: "Length of 'hello'?"
Output: "Length is 5"
```

**Success Criteria:**
- [ ] Code chạy không errors
- [ ] Tất cả tests pass
- [ ] Hiểu flow: input → registry lookup → execution → output

---

### Bài 2: Tạo MCP Server (60-90 min)

**Mục tiêu:** Xây dựng MCP server hoàn chỉnh

**Tasks:**
1. Cài đặt `mcp` library
2. Tạo MCP Server với 4 tools:
   - `get_current_time()` - lấy thời gian hiện tại
   - `format_text(text)` - format text (uppercase, etc.)
   - `count_words(text)` - đếm số từ
   - `reverse_string(text)` - đảo ngược string
3. Implement `@server.call_tool()` handler
4. Implement `@server.list_tools()` handler
5. Test từng tool

**Expected Server Behavior:**
```python
# Server receives
{"method": "tools/call", "params": {"name": "count_words", "arguments": {"text": "hello world"}}}

# Server responds
{"result": {"content": [{"type": "text", "text": "2"}]}}
```

**Success Criteria:**
- [ ] Server khởi tạo thành công
- [ ] @list_tools() trả về 4 tools
- [ ] @call_tool() xử lý tất cả 4 tools đúng
- [ ] Test cases pass

---

### Bài 3: MCP + LangChain Integration (45-60 min)

**Mục tiêu:** Kết nối MCP server với LangChain

**Tasks:**
1. Tạo `MCPClient` class để kết nối với server từ Bài 2
2. Implement `list_available_tools()` - lấy tools từ server
3. Implement `call_tool()` - gọi tool từ server
4. Tạo LangChain StructuredTools từ MCP tools
5. Tạo simple agent sử dụng LangChain + MCP tools
6. Test agent

**Expected Integration:**
```python
mcp_client = MCPClient(server)
mcp_tools = mcp_client.list_available_tools()  # [tool1, tool2, ...]

# Convert to LangChain tools
langchain_tools = []
for tool in mcp_tools:
    lt = StructuredTool(name=tool.name, func=mcp_client.call_tool, ...)
    langchain_tools.append(lt)

# Use in agent
agent = create_react_agent(llm, langchain_tools)
```

**Success Criteria:**
- [ ] MCPClient kết nối với server
- [ ] LangChain tools wrap MCP tools
- [ ] Agent có thể gọi MCP tools
- [ ] Test cases pass

---

### Bài 4: Agentic Chatbot với LangGraph (90-120 min)

**Mục tiêu:** Xây dựng agentic chatbot hoàn chỉnh

**Tasks:**
1. Định nghĩa `AgentState` TypedDict
2. Tạo `StateGraph` workflow
3. Implement `agent_node` - LLM decision making
4. Implement `tool_node` - tool execution
5. Implement `end_node` - final response
6. Add edges và transitions
7. Compile graph
8. Test với multi-turn conversations

**Expected Graph Structure:**
```
START → agent_node
  ↓ (decision loop)
  tool_node ←┐
  ↓          │
  agent_node ┘
  ↓ (final)
  end_node → END
```

**Example Conversation:**
```
User: "What time is it and reverse 'John'?"

Step 1 (agent_node):
- See: user input + MCP tools
- Decide: need 2 tools (get_current_time, reverse_string)

Step 2 (tool_node):
- Execute: get_current_time() → "2024-01-15 14:30:00"
- Execute: reverse_string("John") → "nhoJ"
- Update state with results

Step 3 (agent_node):
- See: previous results
- Decide: ready to answer

Step 4 (end_node):
- Generate: "It's 2024-01-15 14:30:00. Your name reversed is 'nhoJ'"

Output: Response to user
```

**Success Criteria:**
- [ ] Graph compiles tanpa errors
- [ ] Agent dapat handle multi-turn
- [ ] Tools dipanggil dalam urutan yang benar
- [ ] Multi-tool calling bekerja
- [ ] Test cases pass

---

### Bonus: OpenAI Integration (Optional, 60-90 min)

**Mục tiêu:** Kết nối dengan OpenAI API untuk real LLM

**Tasks:**
1. Setup OpenAI client (dengan API key)
2. Convert MCP tools to OpenAI function schema
3. Implement agent loop dengan GPT-4
4. Handle tool calls dari OpenAI
5. Implement streaming (optional)
6. Production error handling

**Example Code:**
```python
from openai import OpenAI
client = OpenAI(api_key="sk-...")

tools_schema = [{
    "type": "function",
    "function": {
        "name": tool.name,
        "description": tool.description,
        "parameters": tool.args_schema
    }
} for tool in mcp_tools]

response = client.chat.completions.create(
    model="gpt-4",
    messages=[...],
    tools=tools_schema
)
```

**Success Criteria:**
- [ ] OpenAI client initialized
- [ ] Tool schema correctly formatted
- [ ] Agent loop works with real LLM
- [ ] Streaming works (optional)
- [ ] Error handling robust

---

## 🎯 Learning Outcomes

Setelah menyelesaikan semua:

✅ **Function Calling**
- Memahami flow lengkap function calling
- Bisa implement dari scratch
- Tahu kapan pakai manual vs API

✅ **MCP Protocol**
- Definisi dan tujuan MCP
- Client-Server architecture
- JSON-RPC message format

✅ **MCP Server Development**
- Buat MCP server dengan mcp library
- Implement tools, resources, prompts
- Handle requests dan responses

✅ **MCP Integration**
- Koneksi LLM dengan MCP server
- Integrate MCP ke LangChain
- Praktik production patterns

✅ **Agentic Systems**
- Design dengan LangGraph
- State management
- Multi-turn conversations
- Tool orchestration

✅ **Production Ready**
- Error handling
- Testing strategies
- Logging dan monitoring
- Deployment patterns

---

## 📊 Knowledge Map

```
Function Calling (Fundamentals)
    ↓
MCP Protocol (Architecture)
    ↓
MCP Server (Implementation)
    ├─ Tools
    ├─ Resources
    └─ Prompts
    ↓
LLM + MCP (Integration)
    ├─ Client
    ├─ Server
    └─ Communication
    ↓
LangChain + MCP (Framework)
    ├─ Tool wrapping
    └─ Agent integration
    ↓
LangGraph + MCP (Advanced)
    ├─ State management
    ├─ Workflow design
    └─ Multi-turn logic
    ↓
Production Systems
    ├─ Error handling
    ├─ Deployment
    └─ Optimization
```

---

## 🔗 Connections to Other Topics

- **Week 4 (Prompt Engineering)**: CoT, ReAct - agent reasoning
- **Week 6 (LangChain)**: Agents, chains, tool use
- **Week 7 (Multi-agent)**: Coordination, communication
- **Week 8 (Production)**: Deployment, scaling, monitoring

---

## 📚 Reference Materials

- MCP Spec: https://modelcontextprotocol.io/spec
- LangChain Docs: https://python.langchain.com
- LangGraph Docs: https://langchain-ai.github.io/langgraph
- OpenAI API: https://platform.openai.com/docs

---

**Status: Ready to Learn! 🚀**
