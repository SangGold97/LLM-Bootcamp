# MCP Learning Path - Quick Start Guide

## 📚 3 Files Bạn Vừa Tạo

```
week5-tool-use/
├── 01_MCP_fundamentals_theory.ipynb     ← Lý thuyết + ví dụ (70% code, 30% explanation)
├── 02_MCP_exercises.ipynb                ← 4 bài tập thực hành (TODO-driven)
└── README_MCP_LEARNING_PATH.md           ← Hướng dẫn chi tiết (tài liệu này)
```

---

## 🎯 Bắt Đầu Ngay

### Bước 1: Cài Đặt Dependencies

```bash
# Mở terminal
pip install mcp langchain-core langgraph openai jupyter ipython python-dotenv
```

### Bước 2: Mở Notebook 1 (Lý Thuyết)

```bash
# Trong thư mục week5-tool-use
jupyter notebook 01_MCP_fundamentals_theory.ipynb
```

**Hoặc** mở trực tiếp trong VS Code:
- Ctrl+P → "01_MCP_fundamentals_theory.ipynb"
- Click trên file

### Bước 3: Chạy Từng Cell

1. **Cell 1**: Đọc introduction
2. **Cell 2-20**: Function Calling cơ bản
   - Chạy → Hiểu output → Chỉnh sửa → Chạy lại
3. **Cell 21-30**: MCP là gì
4. ... tiếp tục

### Bước 4: Hoàn Thành Bài 1 (Notebook 2)

- Mở `02_MCP_exercises.ipynb`
- Hoàn thành TODO 1-6 cho Bài 1
- Test kết quả

---

## 📖 Học Tập Strategy

### Strategy 1: Sequential (Recommend)
```
Phần 1 → Bài 1
  ↓
Phần 2-3 → Bài 1 (xong)
  ↓
Phần 4 → Bài 2
  ↓
Phần 5-6 → Bài 3
  ↓
Phần 7 → Bài 4
  ↓
Bonus → OpenAI Integration
```

### Strategy 2: Theory First
```
Notebook 1 (tất cả phần) → Hiểu complete architecture
  ↓
Notebook 2 (tất cả bài) → Apply knowledge
```

### Strategy 3: Project-Based
```
Bài 4 (LangGraph Agent) → What do I need?
  ↓
Trace back → Bài 2 (MCP Server)
  ↓
Trace back → Bài 1 (Function Calling)
```

---

## 🔍 Cấu Trúc Notebook 1 (Theory)

### Phần 1: Function Calling Cơ Bản (15 min)
```
Khái niệm → Code tools → Registry → Mock LLM → Loop → OpenAI API
```
**Key Takeaway:** LLM gọi functions dựa trên user input

---

### Phần 2: Vấn Đề Thực Tế (10 min)
```
Nhiều LLM formats → Khó maintain → Không có giao thức chung
```
**Key Takeaway:** Cần MCP để standardize

---

### Phần 3: MCP Kiến Trúc (15 min)
```
Định nghĩa → Client-Server → JSON-RPC → Protocol
```
**Key Takeaway:** MCP = standard protocol cho tool calling

---

### Phần 4: MCP Server (20 min)
```
Tạo Server → Tools → Resources → List/Call
```
**Key Takeaway:** Implement server dễ dàng với mcp library

---

### Phần 5: LLM + MCP (10 min)
```
Client → Connect → ListTools → CallTool → Result
```
**Key Takeaway:** MCP message protocol (JSON-RPC)

---

### Phần 6: LangChain + MCP (15 min)
```
MCP Tools → StructuredTool → Agent
```
**Key Takeaway:** LangChain integration dễ dàng

---

### Phần 7: LangGraph + MCP (20 min)
```
State → Agent Node → Tool Node → Loop → End
```
**Key Takeaway:** Complex agentic workflows

---

## 🧪 Cấu Trúc Notebook 2 (Exercises)

### Bài 1: Function Calling Cơ Bản (30-45 min)
```
TODO 1: Tools (add, subtract, get_length)
TODO 2: Registry class
TODO 3: Register tools
TODO 4: Mock LLM
TODO 5: Function calling loop
TODO 6: Tests
```
**Outcome:** Simple function calling system

---

### Bài 2: MCP Server (60-90 min)
```
TODO 1: Install mcp
TODO 2: Create Server
TODO 3: Implement @call_tool()
TODO 4: Implement @list_tools()
TODO 5: 4 tools (time, format, count, reverse)
TODO 6: Tests
```
**Outcome:** Production MCP server

---

### Bài 3: MCP + LangChain (45-60 min)
```
TODO 1: MCPClient class
TODO 2: LangChain Tools từ MCP
TODO 3: Simple agent test
```
**Outcome:** MCP → LangChain integration

---

### Bài 4: LangGraph Agent (90-120 min)
```
TODO 1: AgentState
TODO 2: StateGraph + Nodes
TODO 3: agent_node, tool_node, end_node
TODO 4: Edges + transitions
TODO 5: Test agent
```
**Outcome:** Full agentic chatbot

---

### Bonus: OpenAI Integration (Optional, 60-90 min)
```
Setup OpenAI client
Format MCP tools for OpenAI
Implement agent loop with GPT-4
Handle streaming (optional)
```
**Outcome:** Production-ready system

---

## 💡 Tips Khi Học

### 1. **Chạy Code Cells**
```python
# Không chỉ đọc, hãy chạy code
# Thay đổi values, chạy lại, thấy khác gì
cell.run()  # Ctrl+Enter hoặc Shift+Enter
```

### 2. **Print Debug**
```python
# Thêm print để hiểu flow
print(f"DEBUG: tool_name={tool_name}, args={args}")
print(f"DEBUG: result={result}")
```

### 3. **Viết Comments**
```python
# Khi làm bài tập, comment từng bước
# Giúp bạn hiểu lại sau này
```

### 4. **Thử Lỗi Intentionally**
```python
# Cố tình break code để hiểu error
# "What happens if I pass wrong argument?"
```

---

## ⏱️ Estimated Time

| Phần | Thời Gian |
|------|-----------|
| Notebook 1 (đọc + chạy) | 2-3 hours |
| Bài 1 (complete + test) | 0.5-1 hour |
| Bài 2 (complete + test) | 1-1.5 hours |
| Bài 3 (complete + test) | 0.75-1 hour |
| Bài 4 (complete + test) | 1.5-2 hours |
| Bonus (optional) | 1-1.5 hours |
| **Total** | **8-10 hours** |

---

## 🎓 Success Criteria

### ✅ Hoàn thành Phần 1 khi bạn:
- [ ] Hiểu function calling là gì
- [ ] Có thể giải thích flow: input → LLM decision → tool call → result
- [ ] Biết khi nào dùng manual vs OpenAI API

### ✅ Hoàn thành Bài 1 khi:
- [ ] Code chạy không có errors
- [ ] Test cases pass
- [ ] Hiểu mỗi bước trong function calling loop

### ✅ Hoàn thành Phần 4 khi:
- [ ] Biết MCP là gì
- [ ] Hiểu Client-Server architecture
- [ ] Có thể vẽ lại diagram từ memory

### ✅ Hoàn thành Bài 4 khi:
- [ ] Agentic chatbot có thể handle multi-turn
- [ ] Tool calling hoạt động chính xác
- [ ] Có thể giải thích LangGraph workflow

---

## 🐛 Common Issues & Solutions

### Issue 1: "Module not found"
```bash
# Solution
pip install --upgrade mcp langchain-core langgraph

# Or reinstall
pip uninstall mcp langchain-core langgraph
pip install mcp langchain-core langgraph
```

### Issue 2: "Async errors in Jupyter"
```python
# Solution - use asyncio explicitly
import asyncio
asyncio.run(async_function())

# Or use await directly (newer Jupyter)
await async_function()
```

### Issue 3: "Tool call returns wrong type"
```python
# Check 1: Tool function returns correct type?
def add(a, b) -> float:  # ← Must specify return type
    return a + b

# Check 2: Registry.call_tool() handles returns?
# Check 3: Test with simple values first
```

### Issue 4: "JSON-RPC format error"
```python
# Solution - verify response format
{
    "jsonrpc": "2.0",
    "id": <same as request>,  # ← Important
    "result": <actual result>   # or "error"
}
```

---

## 📞 Need Help?

Jika bingung:
1. Re-read the theory section (Notebook 1)
2. Compare with working code examples
3. Check test cases untuk expected behavior
4. Use print statements untuk debug
5. Google error messages

---

## 🚀 Setelah Selesai

Ide untuk lanjutan:
1. **Real API Integration**: Connect real APIs (database, weather API, etc.)
2. **Advanced Features**: Streaming, batch calls, error retry
3. **Production**: Add logging, monitoring, metrics
4. **Optimization**: Caching, parallel execution, batching
5. **Evaluation**: Use RAGAS untuk evaluate agent quality

---

## 📊 Progress Tracker

```markdown
### Week 1
- [ ] Day 1: Notebook 1 Phần 1-2
- [ ] Day 2: Bài 1 (Function Calling)
- [ ] Day 3: Notebook 1 Phần 3-4
- [ ] Day 4: Bài 2 (MCP Server)
- [ ] Day 5-7: Review + Refinement

### Week 2
- [ ] Day 1: Notebook 1 Phần 5-6
- [ ] Day 2: Bài 3 (LangChain)
- [ ] Day 3: Notebook 1 Phần 7
- [ ] Day 4: Bài 4 (LangGraph)
- [ ] Day 5-7: Bonus + Optimization
```

---

## 🎉 Final Checklist

Sebelum klaim completion:
- [ ] Baca semua teori di Notebook 1
- [ ] Jalankan semua code cells (minimal 1x)
- [ ] Modifikasi nilai dan jalankan lagi
- [ ] Selesaikan semua 4 bài tập
- [ ] Semua tests pass
- [ ] Tulis comments untuk setiap function
- [ ] Bisa jelaskan architecture dari memory

---

**Mulai dari sini: Buka `01_MCP_fundamentals_theory.ipynb` sekarang!**

Good luck! 🚀
