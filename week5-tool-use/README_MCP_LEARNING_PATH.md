# 🎓 MCP Learning Path - Từ Cơ Bản đến Nâng Cao

## 📌 Giới Thiệu

Bạn sẽ học **Model Context Protocol (MCP)** thông qua 2 notebook:

1. **Notebook 1 - Lý Thuyết & Ví Dụ** (`01_MCP_fundamentals_theory.ipynb`)
   - Khái niệm Function Calling
   - Vấn đề thực tế
   - MCP là gì
   - Các ví dụ minh họa chi tiết

2. **Notebook 2 - Bài Tập Thực Hành** (`02_MCP_exercises.ipynb`)
   - 4 bài tập chính
   - 1 bonus challenge
   - Từ cơ bản → nâng cao

---

## 🚀 Lộ Trình Học Tập

### Tuần 1: Cơ Bản Function Calling

```
Thứ 2: Đọc Phần 1 (Notebook 1)
  ↓
Thứ 3: Hoàn thành Bài 1 (Notebook 2) - Function Calling Cơ Bản
  ↓
Thứ 4: Đọc Phần 2-3 (Notebook 1) - Vấn đề + MCP là gì
  ↓
Thứ 5: Hoàn thành Bài 2 (Notebook 2) - MCP Server
  ↓
Thứ 6-7: Review + Thực hành lại
```

### Tuần 2: Framework Integration

```
Thứ 2: Đọc Phần 4-6 (Notebook 1)
  ↓
Thứ 3: Hoàn thành Bài 3 (Notebook 2) - LangChain Integration
  ↓
Thứ 4: Đọc Phần 7 (Notebook 1)
  ↓
Thứ 5: Hoàn thành Bài 4 (Notebook 2) - LangGraph Agent
  ↓
Thứ 6-7: Bonus (OpenAI Integration)
```

---

## 📖 Chi Tiết Từng Notebook

### Notebook 1: 01_MCP_fundamentals_theory.ipynb

**Nội dung:**

| Phần | Tiêu Đề | Học | Thực Hành |
|------|---------|------|----------|
| 1 | Function Calling Cơ Bản | Khái niệm + Code | Mock LLM demo |
| 2 | Vấn đề Thực Tế | Vấn đề + Giải pháp | So sánh |
| 3 | MCP Kiến Trúc | Kiến trúc + Protocol | Diagram |
| 4 | MCP Server | Implementation | Calculator + Weather |
| 5 | LLM + MCP | Client-Server | Message flow |
| 6 | LangChain + MCP | Integration | Tool definition |
| 7 | LangGraph + MCP | Agentic workflows | Full chatbot |

**Cách học:**
1. Đọc từng section
2. Chạy code cells để thấy output
3. Thay đổi values và chạy lại
4. Hiểu rõ mỗi bước trước khi qua phần sau

---

### Notebook 2: 02_MCP_exercises.ipynb

**Bài 1: Function Calling Cơ Bản** (⭐⭐)
- TODO 1: Implement 3 tools (add, subtract, get_length_of_string)
- TODO 2: Tạo ToolRegistry class
- TODO 3: Đăng ký tools
- TODO 4: Mock LLM decision function
- TODO 5: Function calling loop
- TODO 6: Test cases

**Expected:** Bạn có thể gọi tools dựa trên user input

---

**Bài 2: MCP Server** (⭐⭐⭐)
- Implement MCP Server với 4 tools
- Tools: get_current_time, format_text, count_words, reverse_string
- Sử dụng `mcp` library
- Implement @call_tool() và @list_tools()

**Expected:** MCP Server hoàn chỉnh có thể được client kết nối

---

**Bài 3: MCP + LangChain** (⭐⭐⭐)
- Tạo MCPClient
- Tạo LangChain Tools từ MCP Tools
- Integrate MCP vào LangChain

**Expected:** LangChain Agent có thể gọi MCP tools

---

**Bài 4: LangGraph Agentic Chatbot** (⭐⭐⭐⭐)
- Định nghĩa AgentState
- Tạo LangGraph workflow
- Implement agent_node, tool_node, end_node
- Multi-turn conversation support

**Expected:** Agentic chatbot hoàn chỉnh

---

**Bonus: OpenAI Integration** (⭐⭐⭐⭐⭐)
- Kết nối thực với OpenAI API
- Thay mock LLM bằng GPT-4
- Real agent loop

**Expected:** Production-ready agentic system

---

## 🎯 Learning Objectives

Sau khi hoàn thành cả 2 notebook, bạn sẽ:

✅ **Function Calling**
- Hiểu cách LLM gọi tools
- Có thể implement function calling từ scratch
- Biết các tình huống sử dụng

✅ **MCP Server**
- Tạo MCP server với tools, resources, prompts
- Hiểu MCP protocol (JSON-RPC)
- Biết architecture patterns

✅ **MCP Integration**
- Kết nối LLM client với MCP server
- Integrate MCP vào LangChain
- Xây dựng agents sử dụng LangGraph + MCP

✅ **Production Skills**
- Error handling & logging
- Testing & validation
- Deployment & scaling

---

## 🛠️ Tools & Environment

### Cần cài đặt:
```bash
pip install mcp langchain-core langgraph openai
```

### Optional (nhưng recommend):
```bash
pip install jupyter ipython python-dotenv
```

### API Keys (cho Bonus):
- OpenAI API Key: https://platform.openai.com/api-keys
- Anthropic API Key (Claude): https://console.anthropic.com

---

## ✅ Tiêu Chí Hoàn Thành

Mỗi bài tập cần:
- ✨ **Code chạy được** (không có syntax/runtime errors)
- 📝 **Có comments** giải thích logic
- 🧪 **Có test cases** để verify
- 💡 **Hiểu rõ** từng bước (có thể giải thích cho người khác)

---

## 📊 Timeline Suggest

```
Week 1:
- Monday: Notebook 1 Phần 1 + Bài 1
- Tuesday: Notebook 1 Phần 2-3 + Bài 1 (tiếp)
- Wednesday: Notebook 1 Phần 4 + Bài 2
- Thursday: Notebook 2 Bài 2 (tiếp)
- Friday-Sunday: Review + Bonus exercises

Week 2:
- Monday: Notebook 1 Phần 5-6 + Bài 3
- Tuesday: Notebook 2 Bài 3 (tiếp)
- Wednesday: Notebook 1 Phần 7 + Bài 4
- Thursday-Friday: Bài 4 (tiếp) + Bonus
- Saturday-Sunday: Full integration + Optimization
```

---

## 🎓 Sau Khi Hoàn Thành

Bạn có thể:
1. Tạo **MCP server** cho bất kỳ use case nào
2. Xây dựng **agentic systems** sử dụng LLM + MCP
3. Integrate **multi-tool agents** với production frameworks
4. **Deploy** MCP servers và scale chúng
5. Tạo **custom tools** cho LangChain/LangGraph

---

## 💬 Troubleshooting

### Issue: Import errors
```python
# Cài lại packages
pip install --upgrade mcp langchain-core langgraph
```

### Issue: Async errors trong Jupyter
```python
# Sử dụng asyncio.run() hoặc await trực tiếp
import asyncio
asyncio.run(async_function())
```

### Issue: Tool call không hoạt động
```python
# Check:
1. Tool registered vào registry?
2. Tool name match?
3. Arguments format đúng?
4. Return type của tool đúng?
```

---

## 📚 Tài Liệu Tham Khảo

- **MCP Official**: https://modelcontextprotocol.io
- **LangChain Docs**: https://python.langchain.com
- **LangGraph Docs**: https://langchain-ai.github.io/langgraph
- **OpenAI API**: https://platform.openai.com/docs

---

## 🚀 Tiếp Tục Học Tập

Sau hoàn thành:
1. **Deep dive** vào specific use cases (database tools, APIs, etc.)
2. **Optimize** agent performance (caching, batching, streaming)
3. **Evaluate** agents (RAGAS, custom metrics)
4. **Deploy** production systems (Docker, Kubernetes)

---

**Happy Learning! 🎉**

Nếu có câu hỏi hoặc cần giúp đỡ, hãy quay lại và hỏi từng phần cụ thể.
