# 🎓 MCP Learning Path - Complete Package

## 📦 Bạn Vừa Nhận Được Gì?

Một **hoàn chỉnh learning path** từ Function Calling cơ bản → Production MCP Systems

### 📁 Files trong Package

```
week5-tool-use/
├── 📓 01_MCP_fundamentals_theory.ipynb
│   └─ 7 phần lý thuyết + code examples
│   └─ 150+ cells, code-first learning
│
├── 🧪 02_MCP_exercises.ipynb  
│   └─ 4 bài tập + 1 bonus
│   └─ TODO-driven, hands-on learning
│
├── 📖 README_MCP_LEARNING_PATH.md
│   └─ Hướng dẫn chi tiết học tập
│   └─ Timeline, struktur, kriteria sukses
│
├── ⚡ QUICK_START.md
│   └─ Bắt đầu trong 5 menit
│   └─ Setup, tips, troubleshooting
│
├── 📚 DETAILED_CONTENT.md
│   └─ Outline lengkap setiap section
│   └─ Learning outcomes, connections
│
├── 📋 requirements.txt
│   └─ Semua dependencies
│   └─ Install dengan: pip install -r requirements.txt
│
└── 📄 INDEX.md (file ini)
```

---

## 🚀 Mulai dalam 3 Langkah

### Langkah 1: Install Dependencies (2 menit)
```bash
cd /home/sangnv/Desktop/LLM-bootcamp/week5-tool-use
pip install -r requirements.txt
```

### Langkah 2: Buka Notebook 1 (1 menit)
```bash
jupyter notebook 01_MCP_fundamentals_theory.ipynb
```
Atau: Di VS Code, ctrl+P → "01_MCP_fundamentals_theory.ipynb" → open

### Langkah 3: Baca Intro & Jalankan Cell 1 (2 menit)
- Baca title dan overview
- Jalankan Cell 1 (Shift+Enter)
- Pahami output

**Selesai! Anda sudah mulai. Lanjut dengan Cells berikutnya.**

---

## 📊 Learning Structure

### Notebook 1: Lý Thuyết (150 cells)

```
PHẦN 1 (Cells 1-20): Function Calling Cơ Bản
├─ Khái niệm + flow
├─ Code tools (calculator, weather, search)
├─ ToolRegistry class
├─ Mock LLM decision
├─ Function calling loop
└─ Test & demo

PHẦN 2 (Cells 21-30): Vấn Đề Thực Tế
├─ Nhiều LLM, nhiều format
├─ Khó maintain & scale
├─ Tight coupling
├─ Không có giao thức chung
└─ Giải pháp: MCP

PHẦN 3 (Cells 31-50): MCP Kiến Trúc
├─ Định nghĩa MCP
├─ Client-Server architecture
├─ Message flow (JSON-RPC)
├─ Server capabilities
└─ So sánh với function calling

PHẦN 4 (Cells 51-80): MCP Server
├─ Installation & setup
├─ Calculator server
├─ Weather server (advanced)
├─ Tools, resources, prompts
└─ Implementation patterns

PHẦN 5 (Cells 81-100): LLM + MCP
├─ MCPClient class
├─ Tool discovery
├─ Tool execution
├─ Request-response flow
└─ Message protocol

PHẦN 6 (Cells 101-120): LangChain + MCP
├─ StructuredTool integration
├─ MCP → LangChain tools
├─ Agent creation
├─ Workflow demo
└─ Best practices

PHẦN 7 (Cells 121-150): LangGraph + MCP
├─ Agentic chatbot architecture
├─ State management
├─ Node implementation
├─ Multi-turn conversations
└─ Production patterns
```

---

### Notebook 2: Bài Tập (4 exercises)

```
BÀI 1 (30-45 min): Function Calling Cơ Bản
└─ 6 TODOs, test cases

BÀI 2 (60-90 min): MCP Server
└─ Implement 4 tools, @call_tool, @list_tools

BÀI 3 (45-60 min): MCP + LangChain
└─ MCPClient, LangChain tools integration

BÀI 4 (90-120 min): LangGraph Agent
└─ StateGraph, nodes, edges, multi-turn

BONUS (60-90 min, optional): OpenAI Integration
└─ Real LLM with function calling
```

---

## ⏱️ Timeline Saran

### Minggu 1: Dasar
```
Hari 1: 
  - Install dependencies
  - Baca QUICK_START.md
  - Jalankan Notebook 1 Phần 1 (30 min)

Hari 2:
  - Phần 1 (lanjutan) + modifikasi code (1 hour)
  - Mulai Bài 1 (30 min)

Hari 3:
  - Phần 2-3 (45 min)
  - Finish Bài 1 (45 min)

Hari 4:
  - Phần 4 (1 hour)
  - Mulai Bài 2 (30 min)

Hari 5-7:
  - Finish Bài 2 (1.5 hours)
  - Review semua (1 hour)
```

### Minggu 2: Advanced
```
Hari 1:
  - Phần 5-6 (1 hour)
  - Bài 3 (1.5 hours)

Hari 2:
  - Phần 7 (1.5 hours)
  - Bài 4 (1.5 hours)

Hari 3:
  - Finish Bài 4 (1 hour)

Hari 4-5:
  - Bonus (OpenAI integration) - 2 hours

Hari 6-7:
  - Integration test + optimization (2 hours)
```

**Total: 8-10 hours**

---

## 🎯 Apa Yang Akan Anda Pelajari

### Fundamental Concepts
- ✅ Function calling / tool calling
- ✅ MCP protocol dan architecture
- ✅ JSON-RPC message format
- ✅ Client-server patterns

### Implementation Skills
- ✅ Membuat MCP server dari scratch
- ✅ Definisi tools dan resources
- ✅ Error handling dalam tools
- ✅ Tool discovery mechanism

### Framework Integration
- ✅ Integrate MCP dengan LangChain
- ✅ Build agents dengan LangGraph
- ✅ State management dalam agents
- ✅ Multi-turn conversation handling

### Production Ready
- ✅ Logging dan monitoring
- ✅ Error handling strategies
- ✅ Testing patterns
- ✅ Deployment considerations

---

## 📈 Progression Path

```
Novice (Bais 1):
  "Saya bisa membuat function calling sederhana"

Intermediate (Bais 2-3):
  "Saya bisa membuat MCP server dan integrate ke LangChain"

Advanced (Bais 4):
  "Saya bisa membuat production agentic systems dengan LangGraph"

Expert (Bonus):
  "Saya bisa integrate dengan real LLM APIs dan scale"
```

---

## 🎓 Setelah Selesai

Anda akan bisa:
1. **Membuat** MCP servers untuk berbagai use cases
2. **Integrate** MCP ke existing LLM applications
3. **Design** complex agentic workflows
4. **Deploy** production MCP systems
5. **Optimize** untuk performance dan reliability

### Ide Lanjutan:
- Membuat MCP servers untuk real APIs (database, REST, etc.)
- Advanced features: streaming, batching, caching
- Deployment ke cloud (Docker, Kubernetes)
- Evaluation dan monitoring

---

## 💡 Learning Tips

### 1. **Aktif Code**
```
Jangan cuma baca, ketik dan jalankan code
Modifikasi values, lihat hasilnya, mainkan
```

### 2. **Pahami Sebelum Lanjut**
```
Jangan skip, pastikan setiap part jelas
Bisa jelaskan logic ke orang lain?
```

### 3. **Use Print Statements**
```python
print(f"DEBUG: input={input}, decision={decision}")
# Trace flow lewat print
```

### 4. **Buat Notes**
```
Tulis notes in your own words
Gambar diagrams
Jelaskan ke orang lain
```

### 5. **Experiment**
```
"Apa terjadi jika..."
Coba edge cases
Break code intentionally untuk belajar
```

---

## 🐛 Troubleshooting

### Problem: "ModuleNotFoundError"
**Solution:**
```bash
pip install --upgrade mcp langchain-core langgraph
# atau
pip uninstall mcp langchain-core langgraph -y
pip install mcp langchain-core langgraph
```

### Problem: "Async/await errors"
**Solution:** Di Jupyter, gunakan:
```python
import asyncio
asyncio.run(async_function())
```

### Problem: "Tool not found in registry"
**Solution:** Check:
```python
# 1. Tool terdaftar?
print(registry.tools.keys())

# 2. Nama match?
print(f"Mencari: {tool_name}")

# 3. Format arguments?
print(f"Arguments: {arguments}")
```

---

## 📚 Dokumentasi & Referensi

**Official Docs:**
- MCP: https://modelcontextprotocol.io
- LangChain: https://python.langchain.com
- LangGraph: https://langchain-ai.github.io/langgraph

**API Documentation:**
- OpenAI: https://platform.openai.com/docs
- Anthropic Claude: https://docs.anthropic.com

---

## 🔍 File Guide

| File | Tujuan | Baca Kapan |
|------|--------|-----------|
| QUICK_START.md | Mulai cepat | Pertama kali |
| README_MCP_LEARNING_PATH.md | Detailed guide | Sebelum mulai |
| DETAILED_CONTENT.md | Content overview | Sebagai referensi |
| 01_MCP_fundamentals_theory.ipynb | Pelajaran lý thuyết | Hari 1-3 |
| 02_MCP_exercises.ipynb | Praktek coding | Hari 2-7 |
| requirements.txt | Dependencies | Setup awal |

---

## 🚀 Memulai Sekarang

### Option 1: Cepat
```bash
# Langsung ke QUICK_START.md
cat QUICK_START.md
```

### Option 2: Terstruktur
```bash
# Baca README dulu
cat README_MCP_LEARNING_PATH.md
# Kemudian buka notebook
jupyter notebook 01_MCP_fundamentals_theory.ipynb
```

### Option 3: Comprehensive
```bash
# Pahami struktur lengkap
cat DETAILED_CONTENT.md
# Setup environment
pip install -r requirements.txt
# Mulai belajar
jupyter notebook 01_MCP_fundamentals_theory.ipynb
```

---

## ✅ Checklist Sebelum Mulai

- [ ] Python 3.8+ installed
- [ ] pip working
- [ ] VSCode atau Jupyter ready
- [ ] requirements.txt sudah dibaca
- [ ] API key (optional untuk bonus)

---

## 🎉 Selamat!

Anda punya **lengkap learning package** untuk master MCP dari scratch ke production.

**Sekarang mulai dengan:**
1. Baca QUICK_START.md (5 menit)
2. Install requirements (2 menit)
3. Buka Notebook 1 (1 menit)
4. Jalankan Cell 1 (1 menit)
5. Lanjutkan ke Cell 2!

---

## 📞 Need Help?

1. **Pertanyaan conceptual** → Re-read teori section
2. **Error dalam code** → Lihat troubleshooting
3. **Stuck di exercise** → Check expected output
4. **Perlu konteks** → Baca DETAILED_CONTENT.md

---

**Happy Learning! 🚀**

Dimulai dari sini:
```bash
cat QUICK_START.md
```

Atau langsung:
```bash
jupyter notebook 01_MCP_fundamentals_theory.ipynb
```
