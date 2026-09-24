# Codebase RAG - Chat with Your Code Using AI

An intelligent AI-powered assistant that allows developers to interact with their codebase using natural language.

`Python` `FastAPI` `Tests` `Coverage` `License`

Features • Demo • Tech Stack • Quick Start • Architecture

---

## 👨‍🎓 About This Project

This project was built to explore Retrieval-Augmented Generation (RAG), vector search, and applied LLM engineering. It demonstrates practical, hands-on implementation of concepts from Information Retrieval, NLP, and Software Engineering — combining a FastAPI backend, a FAISS-based vector database, and Google's Gemini 2.5 Flash LLM into a working full-stack application.

---

## 🌟 Overview

Codebase RAG is a Retrieval-Augmented Generation (RAG) system built to enable developers to:

- 💬 Chat with their codebase using natural language
- 🔍 Semantically search across thousands of code files
- 🤖 Get AI-powered explanations of complex code
- 📊 Visualize codebase insights with interactive dashboards
- ⚡ Fast queries with ~11ms average response time

Built with vector embeddings, semantic search, and Google's Gemini 2.5 Flash LLM as part of my learning and academic project work.

## ✨ Features

### 🎯 Core Capabilities
- Natural Language Queries: Ask questions in plain English about your codebase
- Semantic Code Search: Find relevant code using meaning, not just keywords
- AI-Powered Explanations: Get detailed explanations of how code works
- Multi-Language Support: Python, JavaScript, Java, C++, Go, and more
- Real-time Indexing: Automatically updates as your codebase changes

### 🚀 Performance
- 4,364+ code chunks indexed with FAISS vector database
- 11ms average query response time
- 45% test coverage with 21/21 tests passing
- Built with error handling and testing best practices in mind

### 🎨 User Interface
- Clean, responsive design with smooth animations
- Interactive dashboard with real-time metrics
- Code syntax highlighting for better readability
- Query history to track your interactions

## 🎬 Demo

### Chat Interface
```
User: "How does Flask routing work in this codebase?"

AI: "In this codebase, Flask routing is implemented using the @app.route() 
decorator to map URL paths to Python functions. The routing system handles 
incoming HTTP requests by matching the URL pattern and executing the 
corresponding view function..."
```

### Key Features in Action
- 💬 Natural conversations about code functionality
- 📂 Ingest repositories with one command
- 💡 Explain code snippets interactively
- 📊 View analytics on indexed codebase

## 🛠️ Tech Stack

**Backend**
- FastAPI - Modern Python web framework
- LangChain - LLM application framework
- FAISS - Facebook AI Similarity Search (vector database)
- Google Gemini 2.5 Flash - State-of-the-art LLM
- Tree-sitter - Code parsing and AST generation

**Frontend**
- Streamlit - Interactive web interface
- Plotly - Data visualization
- Custom CSS - Modern gradient designs

**Infrastructure**
- Python 3.12+ - Modern Python features
- Pytest - Testing
- Docker - Containerization (optional)
- Git - Version control

## 🚀 Quick Start

### Prerequisites
- Python 3.12 or higher
- Git
- Google Gemini API key (free at Google AI Studio)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/saberathena25/codebase-RAG.git
cd codebase-RAG
```

2. **Create virtual environment**
```bash
python3 -m venv codebase-RAG-env
source codebase-rag-env/bin/activate  # On Windows: codebase-RAG-env\Scripts\activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure API keys**
```bash
# Copy example environment file
cp .env.example .env

# Edit .env and add your Gemini API key
# GEMINI_API_KEY= ****************
```

5. **Run the system**
```bash
# Terminal 1: Start API server
python scripts/run_api.py

# Terminal 2: Start frontend
streamlit run frontend/app.py
```

6. **Open in browser**
- Frontend: http://localhost:8501
- API Docs: http://localhost:8000/docs

## 📁 Project Structure

```
codebase-RAG/
├── backend/
│   ├── api/              # FastAPI REST endpoints
│   │   ├── main.py       # Main API application
│   │   └── models.py     # Pydantic models
│   ├── ingestion/        # Repository loading & processing
│   │   ├── github_loader.py
│   │   └── document_loader.py
│   ├── parsing/          # Code parsing & chunking
│   │   ├── chunker.py
│   │   └── language_detector.py
│   ├── retrieval/        # Vector search & embeddings
│   │   ├── embeddings.py
│   │   ├── vector_store.py
│   │   ├── indexer.py
│   │   └── search.py
│   └── llm/             # LLM integration
│       ├── llm_client.py
│       ├── rag_pipeline.py
│       └── query_constructor.py
├── frontend/            # Streamlit UI
│   └── app.py
├── tests/              # Unit & integration tests
│   ├── test_*.py
│   └── conftest.py
├── data/               # Data storage
│   └── vector_store/   # FAISS indexes
├── config/             # Configuration
│   └── settings.py
├── scripts/            # Utility scripts
│   └── run_api.py
├── .env.example        # Environment template
├── requirements.txt    # Python dependencies
└── README.md          # This file
```

## 🏗️ Architecture

### System Design
```
┌─────────────┐
│   Frontend  │ (Streamlit)
│  localhost  │
│    :8501    │
└──────┬──────┘
       │ HTTP Requests
       ▼
┌─────────────┐
│  FastAPI    │ (REST API)
│   Server    │
│  localhost  │
│    :8000    │
└──────┬──────┘
       │
       ├──► 🔍 Query Pipeline
       │    ├─► Vector Search (FAISS)
       │    ├─► Context Retrieval
       │    └─► LLM Generation (Gemini)
       │
       ├──► 📥 Ingestion Pipeline
       │    ├─► Code Loading
       │    ├─► Parsing & Chunking
       │    └─► Vector Indexing
       │
       └──► 💾 Data Layer
            └─► FAISS Vector Store
```

### RAG Pipeline Flow
1. **User Query** → Natural language question
2. **Query Enhancement** → Expand and optimize query
3. **Vector Search** → Find relevant code chunks (FAISS)
4. **Context Building** → Assemble relevant code snippets
5. **LLM Generation** → Gemini generates contextual answer
6. **Response** → AI-powered explanation with sources

## 💡 Usage Examples

### 1. Index a Repository
```bash
curl -X POST http://localhost:8000/ingest \
  -H "Content-Type: application/json" \
  -d '{
    "repo_url": "https://github.com/username/repo",
    "branch": "main"
  }'
```

### 2. Query Your Codebase
```bash
curl -X POST http://localhost:8000/query \
  -H "Content-Type: application/json" \
  -d '{
    "query": "How does authentication work?",
    "language": "python"
  }'
```

### 3. Explain Code Snippet
```bash
curl -X POST http://localhost:8000/explain \
  -H "Content-Type: application/json" \
  -d '{
    "code": "def fibonacci(n): return n if n < 2 else fibonacci(n-1) + fibonacci(n-2)",
    "language": "python"
  }'
```

## 🧪 Testing

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=backend --cov-report=html

# Run specific test file
pytest tests/test_vector_store.py

# View coverage report
open htmlcov/index.html
```

**Current Test Results:**
- ✅ 21/21 tests passing
- 📊 45% code coverage
- ⚡ Fast test execution

## 🔧 Configuration

Key configuration options in `config/settings.py`:

```python
# Vector Store
CHUNK_SIZE = 512              # Code chunk size
CHUNK_OVERLAP = 50            # Overlap between chunks
VECTOR_DIMENSION = 384        # Embedding dimension

# LLM
GEMINI_MODEL = "gemini-2.5-flash"
MAX_TOKENS = 2048             # Max response tokens
TEMPERATURE = 0.3             # Response creativity

# Retrieval
TOP_K = 20                    # Initial retrieval count
TOP_N = 5                     # Final results to use
```

## 📈 Performance Metrics

| Metric | Value |
|---|---|
| Indexed Vectors | 4,364 |
| Query Time | ~11ms avg |
| Index Load Time | <2s |
| Embedding Dimension | 384 |
| Test Coverage | 45% |
| Tests Passing | 21/21 ✅ |

## 📚 What I Learned

- Designing and implementing a RAG pipeline end-to-end (retrieval + generation)
- Working with vector embeddings and similarity search using FAISS
- Building REST APIs with FastAPI and integrating an LLM (Gemini 2.5 Flash)
- Parsing and chunking source code using Tree-sitter
- Writing tests with Pytest and measuring coverage
- Building an interactive frontend with Streamlit and Plotly

## 🗺️ Roadmap

**Phase 1: Core Features** ✅ (Completed)
- [x] Vector-based code search
- [x] Natural language queries
- [x] AI-powered explanations
- [x] Modern web interface
- [x] Real-time indexing

**Phase 2: Enhancements** 🚧 (In Progress)
- [ ] Multi-repository support
- [ ] Code generation capabilities
- [ ] Team collaboration features
- [ ] GitHub integration
- [ ] VSCode extension

**Phase 3: Advanced Features** 🔮 (Planned)
- [ ] Architecture visualization
- [ ] Code quality analysis
- [ ] Automated documentation
- [ ] CI/CD integration

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 🙏 Acknowledgments

- Google Gemini - AI language model
- FAISS - Vector similarity search
- FastAPI - Modern Python web framework
- Streamlit - Interactive UI framework
- Tree-sitter - Code parsing library
