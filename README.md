# AI Finance Management Software

- A comprehensive AI-powered financial management platform that combines RAG, real-time market analysis and intelligent policy analysis.
- It is designed to transform a large, unstructured collection of RBI PDF documents into a searchable, AI-ready knowledge base.

## 🧰 Tech Stack

- **Frontend:** Next.js, React, TypeScript, Tailwind CSS
- **Backend:** Node.js, Express, TypeScript
- **AI Services:** Python, Azure OpenAI, PyTorch / SentenceTransformers, FAISS, LangChain-style retrieval
- **Data Stores:** PostgreSQL, Redis, Neo4j, FAISS vector store
- **Ingestion / Processing:** PDF parsing, text chunking, embedding generation, market data ingestion
- **Deployment / DevOps:** Docker, Docker Compose

## � DevOps Overview

DevOps in this project focuses on automating deployment, maintaining consistent environments, and enabling rapid iteration across frontend, backend, and AI services. The platform uses Docker to containerize each service and Docker Compose to orchestrate local multi-service workflows, ensuring development, testing, and production environments behave consistently.

Key DevOps benefits include:

- Reliable deployment pipeline with containerized services
- Faster iteration through reproducible builds and environment parity
- Easier scaling and maintenance for frontend, backend, and AI workloads
- Improved collaboration between development and operations practices

## �💼 Resume Highlights

- Designed and built AI Finance Management Software with a Next.js frontend and Node.js/Express backend.
- Developed Python-based AI services for Retrieval-Augmented Generation (RAG) using Azure OpenAI, FAISS embeddings, and Neo4j knowledge graph integration.
- Built a document parsing pipeline to convert large, unstructured RBI PDF documents into a searchable, AI-ready knowledge base.
- Implemented scalable portfolio management and market analysis pipelines using PostgreSQL, Redis caching, and real-time market data ingestion.
- Deployed the multi-service architecture with Docker and Docker Compose for reproducible development and production environments.

## 🏗️ System Architecture Diagrams

### 1. Overall System Architecture

```mermaid
graph TB
    subgraph "User Layer"
        U[👤 Users]
        U --> F[Frontend<br/>Next.js + React]
    end

    subgraph "Application Layer"
        F --> B[Backend<br/>Node.js + Express]
        B --> DB[(PostgreSQL<br/>User Data)]
        B --> R[(Redis<br/>Cache)]
        B --> N[(Neo4j<br/>Knowledge Graph)]
    end

    subgraph "AI Services Layer"
        B --> AI[AI Services<br/>Python]
        AI --> RAG[RAG Engine<br/>Document Q&A]
        AI --> KG[Knowledge Graph<br/>Relationships]
        AI --> ING[Data Ingestion<br/>PDF Processing]
    end

    subgraph "Data & Storage Layer"
        RAG --> VS[(FAISS<br/>Vector Store)]
        ING --> FS[(File System<br/>PDFs & Data)]
        KG --> N
        AI --> DB
    end

    subgraph "External Services"
        AI --> AZ[Azure OpenAI<br/>LLM Service]
        B --> MD[Market Data APIs<br/>Real-time Feeds]
    end

    style U fill:#e1f5fe
    style F fill:#f3e5f5
    style B fill:#e8f5e8
    style AI fill:#fff3e0
    style DB fill:#fce4ec
    style R fill:#f3e5f5
    style N fill:#e0f2f1
    style VS fill:#fff8e1
    style FS fill:#f1f8e9
    style AZ fill:#fce4ec
    style MD fill:#e8eaf6
```

### 2. Data Flow Architecture

```mermaid
flowchart TD
    subgraph "Data Sources"
        PDF[RBI PDF Documents<br/>📄]
        MDATA[Market Data APIs<br/>📊]
        UDATA[User Portfolio Data<br/>💼]
    end

    subgraph "Ingestion Pipeline"
        PDF --> P1[Text Extraction<br/>PyPDF2]
        P1 --> P2[Text Chunking<br/>500 chars]
        P2 --> P3[Embedding Generation<br/>SentenceTransformer]
        P3 --> P4[Vector Storage<br/>FAISS/Sklearn]
    end

    subgraph "Processing Layer"
        MDATA --> M1[Data Normalization<br/>Standardization]
        UDATA --> U1[Portfolio Analysis<br/>Risk Assessment]
        P4 --> Q1[Query Processing<br/>Semantic Search]
    end

    subgraph "AI Layer"
        Q1 --> A1[Context Retrieval<br/>Top-K Chunks]
        A1 --> A2[LLM Generation<br/>Azure OpenAI]
        U1 --> A3[Policy Impact<br/>Analysis]
        M1 --> A4[Market Intelligence<br/>Insights]
    end

    subgraph "Output Layer"
        A2 --> O1[Document Answers<br/>💡]
        A3 --> O2[Policy Recommendations<br/>📋]
        A4 --> O3[Market Insights<br/>📈]
    end

    subgraph "Storage Layer"
        P4 --> S1[(Vector Database<br/>Embeddings)]
        U1 --> S2[(PostgreSQL<br/>Portfolio)]
        A3 --> S3[(Neo4j<br/>Relationships)]
        M1 --> S4[(Redis<br/>Cache)]
    end

    style PDF fill:#e3f2fd
    style MDATA fill:#f3e5f5
    style UDATA fill:#e8f5e8
    style P1 fill:#fff3e0
    style P2 fill:#fff3e0
    style P3 fill:#fff3e0
    style P4 fill:#fff3e0
    style M1 fill:#fce4ec
    style U1 fill:#fce4ec
    style Q1 fill:#fce4ec
    style A1 fill:#fff8e1
    style A2 fill:#fff8e1
    style A3 fill:#fff8e1
    style A4 fill:#fff8e1
    style O1 fill:#c8e6c9
    style O2 fill:#c8e6c9
    style O3 fill:#c8e6c9
    style S1 fill:#e0f2f1
    style S2 fill:#e0f2f1
    style S3 fill:#e0f2f1
    style S4 fill:#e0f2f1
```

### 3. RAG Pipeline Flowchart

```mermaid
flowchart LR
    U[User Query]
    U --> I[Input & Preprocessing]
    I --> S[Semantic Search]
    S --> R[Retrieve Top Chunks]
    R --> A[Assemble Context]
    A --> G[Azure OpenAI Generation]
    G --> O[Answer Delivery]

    subgraph DataStores[Data Stores]
        D1[Document Store / PDFs]
        D2[Vector Store / Embeddings]
        D3[Redis Cache]
        D4[Neo4j Knowledge Graph]
    end

    I --> D1
    S --> D2
    R --> D4
    G --> D3
    MD[Market Data APIs] --> S

    style U fill:#bbdefb,stroke:#1e88e5,stroke-width:2px
    style I fill:#fff9c4,stroke:#fdd835,stroke-width:2px
    style S fill:#fff9c4,stroke:#fdd835,stroke-width:2px
    style R fill:#fff9c4,stroke:#fdd835,stroke-width:2px
    style A fill:#fff9c4,stroke:#fdd835,stroke-width:2px
    style G fill:#fff9c4,stroke:#fdd835,stroke-width:2px
    style O fill:#c8e6c9,stroke:#43a047,stroke-width:2px
    style DataStores fill:#e8f5e9,stroke:#4caf50,stroke-width:2px
    style D1 fill:#dcedc8,stroke:#4caf50,stroke-width:1.5px
    style D2 fill:#dcedc8,stroke:#4caf50,stroke-width:1.5px
    style D3 fill:#dcedc8,stroke:#4caf50,stroke-width:1.5px
    style D4 fill:#dcedc8,stroke:#4caf50,stroke-width:1.5px
    style MD fill:#c8e6c9,stroke:#7cb342,stroke-width:1.5px
```

### 4. Component Interaction Diagram

```mermaid
sequenceDiagram
    participant U as User
    participant F as Frontend
    participant B as Backend API
    participant DB as PostgreSQL
    participant R as Redis
    participant AI as AI Services
    participant VS as Vector Store
    participant LLM as Azure OpenAI

    U->>F: Login Request
    F->>B: POST /api/auth/login
    B->>DB: Verify Credentials
    DB-->>B: User Data
    B-->>F: JWT Token
    F-->>U: Dashboard Access

    U->>F: Ask Financial Question
    F->>B: POST /api/ai/query
    B->>AI: Process Query
    AI->>VS: Semantic Search
    VS-->>AI: Relevant Chunks
    AI->>LLM: Generate Answer
    LLM-->>AI: AI Response
    AI-->>B: Formatted Answer
    B->>R: Cache Response
    B-->>F: Answer + Context
    F-->>U: Display Results

    U->>F: View Portfolio
    F->>B: GET /api/portfolio
    B->>R: Check Cache
    R-->>B: Cached Data?
    alt Cache Miss
        B->>DB: Fetch Portfolio
        DB-->>B: Portfolio Data
        B->>R: Store Cache
    end
    B-->>F: Portfolio Data
    F-->>U: Portfolio View

    U->>F: Policy Impact Analysis
    F->>B: POST /api/policy/analyze
    B->>AI: Analyze Impact
    AI->>DB: Get Policy Data
    AI->>LLM: Generate Insights
    LLM-->>AI: Policy Analysis
    AI-->>B: Analysis Results
    B-->>F: Policy Insights
    F-->>U: Impact Dashboard
```

### 4. Deployment Architecture

```mermaid
graph TB
    subgraph "Load Balancer"
        LB[NGINX Load Balancer<br/>🔄]
    end

    subgraph "Frontend Services"
        LB --> F1[Next.js App<br/>Container 1]
        LB --> F2[Next.js App<br/>Container 2]
        LB --> F3[Next.js App<br/>Container 3]
    end

    subgraph "Backend Services"
        F1 --> B1[Express API<br/>Container 1]
        F2 --> B2[Express API<br/>Container 2]
        F3 --> B3[Express API<br/>Container 3]
    end

    subgraph "AI Services"
        B1 --> AI1[Python AI Service<br/>Container 1]
        B2 --> AI2[Python AI Service<br/>Container 2]
        B3 --> AI3[Python AI Service<br/>Container 3]
    end

    subgraph "Databases"
        B1 --> PG[(PostgreSQL<br/>Primary)]
        B2 --> PG
        B3 --> PG

        AI1 --> RD[(Redis Cluster<br/>Cache)]
        AI2 --> RD
        AI3 --> RD

        AI1 --> VS[(FAISS Vector Store<br/>Distributed)]
        AI2 --> VS
        AI3 --> VS
    end

    subgraph "External Services"
        AI1 --> AZ[Azure OpenAI<br/>LLM API]
        AI2 --> AZ
        AI3 --> AZ

        B1 --> MD[Market Data APIs<br/>Real-time Feeds]
        B2 --> MD
        B3 --> MD
    end

    subgraph "Monitoring & Logging"
        LB --> MON[Monitoring Stack<br/>Prometheus + Grafana]
        B1 --> LOG[ELK Stack<br/>Elasticsearch + Kibana]
        AI1 --> LOG
    end

    style LB fill:#e3f2fd
    style F1 fill:#f3e5f5
    style F2 fill:#f3e5f5
    style F3 fill:#f3e5f5
    style B1 fill:#e8f5e8
    style B2 fill:#e8f5e8
    style B3 fill:#e8f5e8
    style AI1 fill:#fff3e0
    style AI2 fill:#fff3e0
    style AI3 fill:#fff3e0
    style PG fill:#fce4ec
    style RD fill:#f3e5f5
    style VS fill:#fff8e1
    style FS fill:#f1f8e9
    style AZ fill:#fce4ec
    style MD fill:#e8eaf6
    style MON fill:#c8e6c9
    style LOG fill:#e0f2f1
```

### 5. AI Pipeline Detailed Architecture

```mermaid
flowchart TD
    subgraph "Input Processing"
        Q[User Query<br/>💬] --> E1[Text Preprocessing<br/>Cleaning & Normalization]
        E1 --> E2[Query Embedding<br/>SentenceTransformer]
    end

    subgraph "Retrieval Phase"
        E2 --> R1[Vector Similarity Search<br/>FAISS/Sklearn]
        R1 --> R2[Top-K Retrieval<br/>k=5 chunks]
        R2 --> R3[Relevance Filtering<br/>Threshold-based]
        R3 --> R4[Context Assembly<br/>Concatenate Chunks]
    end

    subgraph "Generation Phase"
        R4 --> G1[Prompt Engineering<br/>System + Context + Query]
        G1 --> G2[LLM Inference<br/>Azure OpenAI GPT]
        G2 --> G3[Response Post-processing<br/>Formatting & Validation]
    end

    subgraph "Knowledge Integration"
        R4 --> K1[Knowledge Graph Lookup<br/>Entity Relationships]
        K1 --> K2[Context Enrichment<br/>Related Information]
        K2 --> G1
    end

    subgraph "Caching & Optimization"
        E2 --> C1[Query Cache Check<br/>Redis]
        C1 --> C2[Cache Hit?<br/>Return Cached]
        C2 --> R1
        G3 --> C3[Response Caching<br/>Store Results]
    end

    subgraph "Output"
        G3 --> O1[Final Answer<br/>📝]
        C2 --> O1
        O1 --> O2[Confidence Score<br/>📊]
        O1 --> O3[Source Citations<br/>📚]
    end

    style Q fill:#e3f2fd
    style E1 fill:#f3e5f5
    style E2 fill:#f3e5f5
    style R1 fill:#fff3e0
    style R2 fill:#fff3e0
    style R3 fill:#fff3e0
    style R4 fill:#fff3e0
    style G1 fill:#fff8e1
    style G2 fill:#fff8e1
    style G3 fill:#fff8e1
    style K1 fill:#fce4ec
    style K2 fill:#fce4ec
    style C1 fill:#e8f5e8
    style C2 fill:#e8f5e8
    style C3 fill:#e8f5e8
    style O1 fill:#c8e6c9
    style O2 fill:#c8e6c9
    style O3 fill:#c8e6c9
```

## 🔧 Azure OpenAI RAG Setup

This repository uses a Retrieval-Augmented Generation (RAG) pipeline built in `ai-services/rag/`.
The query flow combines semantic search over FAISS embeddings with Azure OpenAI text generation.

### Key files
- `ai-services/rag/llm.py` — Azure OpenAI client wrapper with real and mock modes
- `ai-services/rag/test_query.py` — end-to-end query test harness
- `ai-services/rag/.env` — local Azure config for `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, and `AZURE_OPENAI_DEPLOYMENT_NAME`

### Required environment variables
```env
AZURE_OPENAI_API_KEY=<your-azure-openai-key>
AZURE_OPENAI_ENDPOINT=https://<your-resource-name>.openai.azure.com/
AZURE_OPENAI_DEPLOYMENT_NAME=gpt-4-1
```

> Note: the endpoint should be the base Azure resource URL only, not the full `/openai/responses` path.

### Real Azure OpenAI usage
By default the project now uses real Azure OpenAI for answer generation.
To run the sample query flow with Azure OpenAI:

```powershell
python ai-services/rag/test_query.py
```

If you want to force the local mock path instead:

```powershell
$env:USE_MOCK=1
python ai-services/rag/test_query.py
```

### Azure RAG query flow
```mermaid
flowchart LR
    U[User Query]<-->F[Frontend / CLI]
    F-->B[Backend API / Test Harness]
    B-->AI[AI Service: RAG Engine]
    AI-->VS[Vector Search (FAISS)]
    VS-->AI
    AI-->AZ[Azure OpenAI GPT-4-1]
    AZ-->AI
    AI-->B
    B-->U

    style U fill:#e1f5fe
    style F fill:#f3e5f5
    style B fill:#e8f5e8
    style AI fill:#fff3e0
    style VS fill:#fff8e1
    style AZ fill:#fce4ec
```

### What this implementation does
1. Loads `.env` values into environment variables
2. Initializes `AzureLLM` with the provided Azure OpenAI config
3. Runs semantic search using `RAGQueryEngine.search_chunks()`
4. Sends the assembled context to Azure OpenAI via `AzureLLM.generate()`
5. Prints the generated answer in `test_query.py`

### Notes
- `gpt-4-1` is the current preferred deployment name for Azure OpenAI in this repo
- The code supports mock mode via `USE_MOCK=1` to avoid costs during development
- If real Azure OpenAI fails, verify deployment name and endpoint in `ai-services/rag/.env`

## ⚙️ LLM Cost Control / “LLM not called” mode

To avoid API costs, the system has a deliberate bypass mode where the LLM inference call is skipped when external AI usage should be blocked.

- config env var or runtime check: `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_DEPLOYMENT_NAME`, and `AZURE_OPENAI_ENDPOINT` missing/placeholder, or `AI_OFFLINE_MODE=true`
- fallback behavior: return cached or default content, and/or return explicit cost-control response (e.g. `LLM disabled for cost control`)
- file reference: `ai-services/rag/llm.py`, `ai-services/rag/test_query.py`, `ai-services/rag/vector_store.py`

### Use cases

1. Local development without incurring token charges
2. Automated unit tests and CI/CD dry runs
3. Initial deployment when keys are not yet provisioned
4. Data pipeline evaluation (embedding + search) without generated text costs

### Implementation hints

- `if not credentials_valid: return fallback_response`
- `if os.getenv('AI_OFFLINE_MODE', 'false').lower() == 'true':` skip Azure OpenAI calls
- Cache and local mock response paths should mirror production output shape

### Example response path

1. User query enters pipeline
2. Vector search returns relevant chunks
3. LLM call is blocked by cost-control guard
4. System returns pre-defined or cached answer

### Benefits

- Zero external token spend in controlled environments
- Faster local/CI test cycles with deterministic output
- Safe progression in staged CI/CD deployments

### Drawback note

- Responses are not generative and may be stale; use this mode for validation only.

## 🧠 Fine-Tuning and Knowledge Graph Integration

### Fine-tuning (LoRA / custom model tuning)

- Files: `ai-services/finetune/` (`config.yaml`, `train_lora.py`)
- Use case: adapt generic language model behavior to financial policy and RBI domain language
- Process: prepare training examples from domain docs -> run LoRA training -> save adapter weights -> load in RAG inference
- Benefits: higher relevance, domain consistency, controlled risk vocabulary

### Knowledge Graph in pipeline

- Files: `ai-services/knowledge-graph/` (`kg_loader.py`, `relations.py`)
- Engine: Neo4j (structured entity relationships from policies, portfolio elements, macro indicators)
- Integration:
  1. Ingestion builds graph nodes/edges from parsed policies and market events
  2. Query pipeline uses graph lookup for entity relations + context enrichment
  3. RAG context assembly merges KG insights with text chunks before LLM prompt
- Use case: policy impact analysis, relation-aware recommendations, risk propagation paths

### Why this matters

- Fine-tuning + KG => precision for financial decision support, with explainable links from graph context.
- Graph connectedness lets pipeline reason in terms of entities and events, not only text similarity.

### 6. Database Schema Architecture

```mermaid
erDiagram
    USERS ||--o{ PORTFOLIOS : owns
    USERS ||--o{ USER_PREFERENCES : has
    USERS ||--o{ QUERY_HISTORY : generates

    PORTFOLIOS ||--o{ PORTFOLIO_HOLDINGS : contains
    PORTFOLIOS ||--o{ PORTFOLIO_ANALYTICS : generates
    PORTFOLIOS ||--o{ RISK_ASSESSMENTS : undergoes

    POLICIES ||--o{ POLICY_IMPACTS : affects
    POLICIES ||--o{ PORTFOLIO_POLICY_IMPACTS : influences

    MARKET_DATA ||--o{ PORTFOLIO_ANALYTICS : feeds
    MARKET_DATA ||--o{ RISK_ASSESSMENTS : informs

    DOCUMENTS ||--o{ DOCUMENT_CHUNKS : divided_into
    DOCUMENT_CHUNKS ||--o{ EMBEDDINGS : generates
    EMBEDDINGS ||--o{ QUERY_HISTORY : matches

    KNOWLEDGE_GRAPH {
        string entity_id PK
        string entity_type
        json properties
        datetime created_at
        datetime updated_at
    }

    KNOWLEDGE_GRAPH ||--o{ RELATIONSHIPS : connects
    RELATIONSHIPS ||--o{ KNOWLEDGE_GRAPH : relates_to

    USERS {
        uuid user_id PK
        string email UK
        string password_hash
        string first_name
        string last_name
        datetime created_at
        datetime last_login
        boolean is_active
    }

    PORTFOLIOS {
        uuid portfolio_id PK
        uuid user_id FK
        string name
        decimal total_value
        string currency
        datetime created_at
        datetime updated_at
    }

    POLICIES {
        uuid policy_id PK
        string title
        text content
        string category
        date effective_date
        json metadata
        datetime created_at
    }

    DOCUMENTS {
        uuid document_id PK
        string filename
        string file_path
        string document_type
        text extracted_text
        json metadata
        datetime uploaded_at
        datetime processed_at
    }

    style USERS fill:#e3f2fd
    style PORTFOLIOS fill:#f3e5f5
    style POLICIES fill:#e8f5e8
    style DOCUMENTS fill:#fff3e0
    style KNOWLEDGE_GRAPH fill:#fce4ec
```

## 📋 Core Components

### 🎨 Frontend (Next.js + React)
- **Location**: `frontend/`
- **Tech Stack**: Next.js 16, React 19, TypeScript, Tailwind CSS
- **Features**:
  - User authentication and registration
  - Dashboard with portfolio analytics
  - Policy impact analysis
  - Interactive charts and data visualization
  - Real-time market data display

### 🚀 Backend (Node.js + Express)
- **Location**: `backend/`
- **Tech Stack**: Node.js, Express, TypeScript
- **API Routes**:
  - `/auth` - User authentication
  - `/ai` - AI-powered insights
  - `/policy` - Policy analysis
  - `/portfolio` - Portfolio management
- **Services**:
  - Neo4j for knowledge graph
  - PostgreSQL for structured data
  - Redis for caching

### 🤖 AI Services (Python)
- **Location**: `ai-services/`
- **Components**:

#### RAG (Retrieval-Augmented Generation)
- **Location**: `ai-services/rag/`
- **Purpose**: Intelligent document Q&A system
- **Components**:
  - `llm.py` - Azure OpenAI integration
  - `vector_store.py` - FAISS/sklearn vector storage
  - `query.py` - RAG query engine
  - `embedder.py` - Text embedding generation

#### Knowledge Graph
- **Location**: `ai-services/knowledge-graph/`
- **Purpose**: Financial relationship modeling
- **Components**:
  - `kg_loader.py` - Graph data loading
  - `relations.py` - Entity relationship extraction

#### Data Ingestion Pipeline
- **Location**: `ai-services/ingestion/`
- **Purpose**: Process and index financial documents
- **Components**:
  - `pdf_parser.py` - RBI PDF document parsing
  - `chunker.py` - Text chunking for embeddings
  - `pipeline.py` - Complete ingestion workflow
  - `rbi_pdf_crawler.py` - RBI document crawling

#### Orchestration Layer
- **Current Implementation**: Custom-built orchestration using direct API calls and manual pipeline management
- **Definition**: A bespoke system designed specifically for this project to coordinate and manage the interactions between various AI and data processing components. Unlike using off-the-shelf frameworks (like LangChain), it involves manually implementing the logic for chaining operations, data flow, and component integration.
- **LangChain Status**: Not currently integrated (listed in `ai-services/rag-services/requirements.txt` but not implemented)
- **Purpose**: Streamline AI component interactions, chain multiple operations, and manage complex workflows

##### How to Add LangChain Integration
1. **Install Dependencies**: LangChain is already in `ai-services/rag-services/requirements.txt`
2. **Refactor RAG Pipeline**: Replace custom `query.py` with LangChain's `RetrievalQA` chain
3. **Integrate Components**: Use LangChain's vector stores, embeddings, and LLM wrappers
4. **Example Implementation**:
   ```python
   from langchain.chains import RetrievalQA
   from langchain.vectorstores import FAISS
   from langchain.embeddings import SentenceTransformerEmbeddings
   from langchain.llms import AzureOpenAI

   # Create LangChain components
   embeddings = SentenceTransformerEmbeddings(model_name="all-MiniLM-L6-v2")
   vectorstore = FAISS.load_local("data/embeddings", embeddings)
   llm = AzureOpenAI(...)  # Configure with Azure credentials
   
   # Create RAG chain
   qa_chain = RetrievalQA.from_chain_type(
       llm=llm,
       chain_type="stuff",
       retriever=vectorstore.as_retriever()
   )
   
   # Use the chain
   result = qa_chain.run("What is RBI's current repo rate?")
   ```

##### Benefits of LangChain Integration
- **Modularity**: Pre-built components for common AI tasks (embedding, vector storage, LLM calls)
- **Chain Composition**: Easily combine multiple AI operations into complex workflows
- **Standardization**: Consistent interfaces across different AI providers and tools
- **Rapid Prototyping**: Quick setup of RAG, conversational AI, and agent systems
- **Ecosystem**: Access to LangChain's extensive library of integrations and tools
- **Maintainability**: Less custom code, more focus on business logic
- **Scalability**: Built-in support for streaming, async operations, and distributed processing

### 🗄️ Data Layer

#### PostgreSQL Database
- User accounts and preferences
- Portfolio data and transactions
- Policy information and analysis

#### Redis Cache
- Session management
- Frequently accessed market data
- API response caching

#### FAISS Vector Store
- Document embeddings for semantic search
- Fast similarity search capabilities
- Scalable vector indexing

## 🔄 Data Flow & Processes

### 1. Document Ingestion Process
```
RBI PDFs → PDF Parser → Text Chunker → Embeddings → FAISS Index
     ↓           ↓           ↓           ↓           ↓
Raw Data → Structured → Chunks → Vectors → Searchable
```

### 2. Query Processing Pipeline
```
User Query → Embedding → Vector Search → Context Retrieval → LLM Generation → Answer
     ↓           ↓           ↓           ↓           ↓           ↓
   Input → Semantic → Relevant → Knowledge → AI Response → Final
           Search    Chunks     Context     Generation    Answer
```

### 3. Portfolio Analysis Workflow
```
Market Data → Risk Assessment → Policy Impact → AI Insights → Recommendations
     ↓           ↓           ↓           ↓           ↓
Real-time → Analysis → Evaluation → Generation → Personalized
   Feeds      Engine     Engine      Engine       Advice
```

## 🚀 Quick Start

### Prerequisites
- Docker & Docker Compose
- Node.js 18+
- Python 3.8+
- Azure OpenAI account (for AI features)

### 1. Clone and Setup
```bash
git clone <repository-url>
cd ai-finance-management-software
```

### 2. Environment Configuration
```bash
# Copy and configure environment files
cp backend/.env.example backend/.env
cp frontend/.env.example frontend/.env
cp ai-services/rag/.env.example ai-services/rag/.env

# Edit .env files with your credentials
```

### 3. Launch with Docker
```bash
# Start all services
docker-compose -f devops/docker-compose.yml up -d

# Or for development
docker-compose -f devops/docker-compose.dev.yml up
```

### 4. Manual Development Setup

#### Backend Setup
```bash
cd backend
npm install
npm run dev
```

#### Frontend Setup
```bash
cd frontend
npm install
npm run dev
```

#### AI Services Setup
```bash
cd ai-services
pip install -r requirements.txt
cd rag
python test_query.py  # Test RAG system
```

## 🔧 Configuration

### Azure OpenAI Setup
Create `.env` file in `ai-services/rag/`:
```env
AZURE_OPENAI_API_KEY=your_api_key_here
AZURE_OPENAI_ENDPOINT=https://your-resource.openai.azure.com/
AZURE_OPENAI_DEPLOYMENT_NAME=your_deployment_name
```

### Database Configuration
Update `backend/.env`:
```env
DATABASE_URL=postgresql://user:password@localhost:5432/finance_db
REDIS_URL=redis://localhost:6379
```

## 📊 Key Features

### 🤖 AI-Powered Insights
- **Document Q&A**: Ask questions about financial documents
- **Policy Analysis**: Understand policy impacts on portfolios
- **Market Intelligence**: AI-driven market analysis
- **Risk Assessment**: Automated risk evaluation

### 📈 Portfolio Management
- **Real-time Tracking**: Live portfolio monitoring
- **Performance Analytics**: Comprehensive performance metrics
- **Risk Management**: Automated risk assessment
- **Rebalancing**: Intelligent portfolio optimization

### 📋 Policy Impact Analysis
- **Regulatory Monitoring**: Track policy changes
- **Impact Assessment**: Evaluate policy effects
- **Compliance Checking**: Automated compliance verification
- **Scenario Planning**: Policy change simulations

## 🛠️ Development Workflow

### Code Quality
```bash
# Frontend linting
cd frontend && npm run lint

# Backend type checking
cd backend && npm run build

# AI services testing
cd ai-services/rag && python test_query.py
```

### Testing Strategy
- **Unit Tests**: Component-level testing
- **Integration Tests**: API endpoint testing
- **E2E Tests**: Full user workflow testing
- **AI Model Tests**: RAG system validation

### Deployment Pipeline
```bash
# Build all services
docker-compose build

# Run tests
docker-compose -f docker-compose.test.yml up

# Deploy to production
docker-compose -f docker-compose.prod.yml up -d
```

## 🔒 Security Considerations

- **API Key Management**: Secure storage of Azure OpenAI keys
- **Data Encryption**: End-to-end encryption for sensitive data
- **Authentication**: JWT-based user authentication
- **Rate Limiting**: API rate limiting and abuse prevention
- **Audit Logging**: Comprehensive activity logging

## 📈 Monitoring & Analytics

- **Performance Metrics**: Response times and throughput
- **Error Tracking**: Centralized error monitoring
- **Usage Analytics**: User behavior and feature usage
- **AI Model Metrics**: RAG system performance tracking

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

### Development Guidelines
- Follow TypeScript/JavaScript best practices
- Write comprehensive tests
- Update documentation for API changes
- Ensure all CI/CD checks pass

## 📝 API Documentation

### Backend APIs
- `GET /api/auth/me` - Get current user
- `POST /api/portfolio/analyze` - Analyze portfolio
- `GET /api/policy/impacts` - Get policy impacts
- `POST /api/ai/query` - AI-powered queries

### AI Service APIs
- `POST /api/rag/query` - Document Q&A
- `POST /api/embeddings/generate` - Generate embeddings
- `GET /api/knowledge-graph/search` - Graph search

## 🐛 Troubleshooting

### Common Issues

**RAG System Not Working**
```bash
# Check vector store
cd ai-services/rag
python -c "from vector_store import VectorStore; vs = VectorStore(); vs.load()"

# Verify embeddings exist
ls -la data/embeddings/
```

**Database Connection Issues**
```bash
# Check PostgreSQL
docker-compose logs postgres

# Test Redis connection
docker-compose exec redis redis-cli ping
```

**Azure OpenAI Errors**
```bash
# Verify environment variables
cd ai-services/rag
python load_env.py
python -c "from llm import AzureLLM; llm = AzureLLM(); print('LLM ready')"

## ⚡ Latency Management

This project is designed to minimize query latency and provide useful responses quickly. Key strategies used:

- **Fast retrieval:** Use FAISS for approximate nearest-neighbor search and limit Top-K (e.g. k=5) to reduce retrieval time.
- **Caching:** Cache frequent query results and precomputed summaries in Redis to serve repeat requests instantly.
- **Asynchronous & parallel execution:** Run embedding generation, vector search, and external API calls in parallel where possible; use non-blocking I/O and background workers for long-running tasks.
- **Batching and rate control:** Batch external API calls (market data, LLM) when serving multiple related queries and enforce rate limits with exponential backoff and retries.
- **Progressive responses & streaming:** Stream partial answers to the client for long LLM generations (via WebSockets or SSE) so users see immediate progress.
- **Prioritization & timeouts:** Prioritize lightweight signals (cache hits, KG hints) and set strict timeouts for slow components with graceful fallbacks to shorter, less expensive answers.
- **Local fallbacks:** Serve cached or heuristic answers when external services are slow or unavailable to preserve responsiveness.
- **Observability:** Measure end-to-end latency (P50/P95/P99), use Grafana/Prometheus dashboards, and alert on latency regressions.

Where to tune in this repo:

- Redis cache keys/TTLs: backend cache layer configuration
- FAISS Top-K and index parameters: `ai-services/rag/vector_store.py`
- LLM timeouts and streaming options: `ai-services/rag/llm.py`
- Worker concurrency and queue settings: orchestration layer and background workers

These knobs let you balance freshness, cost, and responsiveness for your deployment and workload.

```

### Recently Fixed Issues

**❌ AzureLLM Configuration Missing**
- **Problem**: `ValueError: AzureLLM configuration missing: set AZURE_OPENAI_API_KEY...`
- **Root Cause**: Code was using hardcoded environment variable names instead of proper ones
- **Fix**: Updated `llm.py` to use correct env vars: `AZURE_OPENAI_API_KEY`, `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_DEPLOYMENT_NAME`
- **Status**: ✅ Resolved

**❌ FAISS Module Not Found**
- **Problem**: `ModuleNotFoundError: No module named 'faiss'`
- **Root Cause**: FAISS library not installed in environment
- **Fix**: Added fallback implementation using `sklearn.metrics.pairwise.cosine_similarity` when FAISS unavailable
- **Status**: ✅ Resolved with graceful degradation

**❌ Vector Store Loading Issues**
- **Problem**: Model loading hangs on import due to eager initialization
- **Root Cause**: `SentenceTransformer` model loaded at module level
- **Fix**: Implemented lazy loading pattern in `VectorStore` class
- **Status**: ✅ Resolved with faster imports

**❌ Test Script Credential Issues**
- **Problem**: Tests fail when Azure OpenAI credentials not available
- **Root Cause**: Test script required real API keys to run
- **Fix**: Modified `test_query.py` to use dummy credentials and skip LLM calls for testing
- **Status**: ✅ Resolved with credential-independent testing

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙋 Support

For support and questions:
- Create an issue in the repository
- Check the troubleshooting section
- Review the API documentation

---

**Built with ❤️ for intelligent financial management**

**Key Features:**
- **Architecture:** DistilBERT-based with a MiniLM head, 6 transformer layers
- **Embedding Size:** 384 dimensions
- **Training:** Fine-tuned on large-scale datasets for semantic textual similarity and natural language inference
- **Use Cases:** Semantic search, question answering, duplicate detection, clustering, and more
- **Advantages:** Fast inference, low memory usage, and strong performance for English-language tasks

**Role in This Project:**
In the AI PDF Ingestion Pipeline, each chunk of extracted text is embedded using the `all-MiniLM-L6-v2` model. These embeddings capture the semantic meaning of the text, enabling the system to perform efficient and accurate similarity searches. This allows downstream AI applications to retrieve the most relevant information from a large corpus of documents, supporting advanced analytics, semantic search, and AI-driven insights.

**References:**
- [Sentence Transformers Documentation](https://www.sbert.net/docs/pretrained_models.html)
- [all-MiniLM-L6-v2 Model Card on Hugging Face](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)

### Example Usage
To run the pipeline and process all PDFs:

```sh
C:/Python313/python.exe ai-services/ingestion/pipeline.py
```

This will process all PDFs, chunk and embed their text, and save the resulting vector database for use in downstream AI applications.

## Descriptive Analysis: AI PDF Ingestion Pipeline

### What Does This Pipeline Do?
This pipeline is designed to transform a large, unstructured collection of RBI (Reserve Bank of India) PDF documents into a structured, searchable, and AI-ready knowledge base. It automates the process of extracting information from hundreds of regulatory, financial, and policy documents, making this data instantly accessible for advanced analytics, search, and AI-driven applications.

### Why Is This Important?
- **Unlocks Unstructured Data**: Most valuable financial and regulatory information is locked in PDFs. Manual extraction is slow, error-prone, and not scalable. This pipeline automates the process, enabling rapid, repeatable, and accurate data extraction.
- **Foundation for AI & RAG**: By converting documents into vector embeddings, the pipeline enables semantic search and retrieval-augmented generation (RAG). This means you can build AI systems that answer questions, summarize content, or generate insights directly from your document corpus.
- **Scalable & Robust**: The pipeline is built to handle hundreds (or thousands) of documents, with error handling to skip problematic files and continue processing. It is modular, so you can easily add new document types or processing steps.
- **Business Value**: Enables instant access to regulatory knowledge, supports compliance, research, and decision-making, and can power chatbots, search engines, and analytics dashboards for finance professionals.

### How Does It Work? (Step-by-Step)
1. **Document Discovery**: Scans the specified directory for all PDF files, ensuring no document is missed.
2. **Text Extraction**: Uses PyPDF2 to extract raw text from each PDF, regardless of formatting or layout.
3. **Chunking**: Splits the extracted text into smaller, manageable pieces (chunks). This is crucial for embedding and retrieval, as it allows the system to find and return only the most relevant parts of a document.
4. **Embedding**: Each chunk is converted into a high-dimensional vector using a state-of-the-art language model (SentenceTransformer). These vectors capture the semantic meaning of the text, enabling powerful similarity search.
5. **Vector Store**: All vectors and their corresponding text are stored in a FAISS index (for fast similarity search) and a pickle file (for text retrieval).
6. **Saving**: The vector database is saved to disk, ready for use in downstream applications.
7. **Error Handling**: If a file is missing, corrupted, or cannot be processed, it is skipped and logged, ensuring the pipeline completes without interruption.

### Technical Highlights
- **PyPDF2**: Handles a wide range of PDF formats, including scanned and complex documents.
- **SentenceTransformers**: Provides robust, context-aware embeddings for semantic search and AI tasks.
- **FAISS**: Enables lightning-fast vector similarity search, even with large datasets.
- **Modular Design**: Each step can be extended or replaced (e.g., swap in OCR for scanned PDFs, or use a different embedding model).

### Example Use Cases
- **Semantic Search**: Instantly find relevant paragraphs or sections across hundreds of RBI documents by meaning, not just keywords.
- **Regulatory Q&A**: Power chatbots or virtual assistants that answer compliance or policy questions using the actual RBI documents as a knowledge base.
- **Automated Summarization**: Generate summaries or insights from large document sets for analysts or decision-makers.
- **Compliance Monitoring**: Track changes in regulations or policies over time by comparing document embeddings.

### Scalability & Extensibility
- **Handles Large Volumes**: Designed for hundreds or thousands of documents and can be parallelized for even greater speed.
- **Easy to Update**: New documents can be added by simply re-running the pipeline or processing only new files.
- **Customizable**: Chunking strategy, embedding model, and storage format can be tailored to your needs.

### Pitch Value (How to Sell This)
- **Transforms Document Chaos into Knowledge**: Converts a messy, unstructured document repository into a structured, AI-ready asset.
- **Drives Efficiency**: Saves countless hours of manual work, reduces errors, and accelerates research and compliance workflows.
- **Enables Next-Gen AI**: Lays the groundwork for advanced AI features like chatbots, semantic search, and automated analytics.
- **Future-Proof**: Built on open-source, industry-standard tools, ensuring long-term maintainability and flexibility.

---
#   F i n a n c e - A d v i s o r  
 