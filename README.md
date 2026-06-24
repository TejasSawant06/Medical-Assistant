🩺 MedAssist AI – RAG Medical Assistant

An AI-powered Medical Assistant built using Retrieval-Augmented Generation (RAG) that enables users to upload medical documents and receive accurate, context-aware answers grounded in the uploaded content.

🧠 Project Overview

This application is a Medical Domain Chatbot built using Retrieval-Augmented Generation (RAG). Users can upload their own medical documents (textbooks, notes, research papers, reports, etc.), and the system intelligently retrieves the most relevant information before generating a response.

Unlike traditional chatbots, responses are grounded in the uploaded knowledge base, significantly reducing hallucinations and improving factual accuracy.

🎓 What is RAG?

Retrieval-Augmented Generation (RAG) is an AI architecture that combines:

Information Retrieval → Fetches relevant knowledge from external documents.
Large Language Models (LLMs) → Generates natural language responses using the retrieved context.

This approach improves:

Accuracy
Explainability
Domain-specific reasoning
Reduced hallucinations

making it ideal for healthcare and medical applications.

🔄 Architecture
                    User Query
                         │
                         ▼
                Query Embedding
                         │
                         ▼
                Pinecone Vector DB
                         ▲
                         │
       Embedded Chunks ← Chunking ← PDF Loader
                         │
                         ▼
                Retrieved Documents
                         │
                         ▼
         LangChain RAG Pipeline + Groq LLM
                         │
                         ▼
              Context-Aware Response

For a detailed architecture diagram, refer to:

📄 MedicalAssistant.pdf

✨ Features
📄 Upload one or multiple medical PDFs
🔍 Semantic search over uploaded documents
🧩 Automatic text extraction and chunking
🧠 Context-aware question answering
⚡ Fast response generation using Groq LLM
📚 Retrieval-Augmented Generation (RAG)
🌐 FastAPI REST APIs
💬 Interactive Streamlit frontend
☁️ Cloud deployment using Render
🛠️ Tech Stack
Component	Technology
LLM	Groq API (LLaMA 3-70B)
Embeddings	Google Generative AI Embeddings
Vector Database	Pinecone
RAG Framework	LangChain
Backend	FastAPI
Frontend	Streamlit
Deployment	Render
Language	Python
📚 API Endpoints
Upload PDFs
POST /upload_pdfs/

Upload one or more PDF documents.

Ask Questions
POST /ask/
Form Data
{
  "question": "What are the symptoms of diabetes?"
}
Response
{
  "answer": "The uploaded document states that..."
}
📁 Folder Structure
medicalAssistant/
│
├── assets/
│   ├── DIABETES.pdf
│   ├── MedicalAssistant.pdf
│   └── medicalAssistant.png
│
├── client/
│   ├── components/
│   │   ├── chatUI.py
│   │   ├── history_download.py
│   │   └── upload.py
│   │
│   ├── utils/
│   │   └── api.py
│   │
│   ├── app.py
│   ├── config.py
│   └── requirements.txt
│
├── server/
│   ├── middlewares/
│   │   └── exception_handlers.py
│   │
│   ├── modules/
│   │   ├── llm.py
│   │   ├── load_vectorstore.py
│   │   ├── pdf_handlers.py
│   │   └── query_handlers.py
│   │
│   ├── routes/
│   │   ├── ask_question.py
│   │   └── upload_pdfs.py
│   │
│   ├── uploaded_docs/
│   │
│   ├── logger.py
│   ├── main.py
│   ├── requirements.txt
│   └── .env
│
└── README.md
⚡ Quick Setup
1. Clone Repository
git clone https://github.com/TejasSawant06/Medical-Assistant.git
cd Medical-Assistant
2. Backend Setup
cd server

# Create Virtual Environment
python -m venv venv

# Activate Environment

# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate

# Install Dependencies
pip install -r requirements.txt
Create .env file
GOOGLE_API_KEY=your_google_api_key

GROQ_API_KEY=your_groq_api_key

PINECONE_API_KEY=your_pinecone_api_key
Run FastAPI Server
uvicorn main:app --reload --port 8000

Backend URL:

http://localhost:8000
3. Frontend Setup
cd client

# Create Virtual Environment
python -m venv venv

# Activate Environment

# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate

# Install Dependencies
pip install -r requirements.txt
Run Streamlit Application
streamlit run app.py

Frontend URL:

http://localhost:8501
📸 Application Workflow
Step 1

Upload medical documents (PDFs)

Step 2

Text is extracted and split into chunks

Step 3

Embeddings are generated using Google Generative AI

Step 4

Vectors are stored in Pinecone

Step 5

User asks a medical question

Step 6

Relevant chunks are retrieved

Step 7

Groq LLaMA 3 generates a context-aware response

☁️ Deployment

The application is deployed on Render.

Start Command
uvicorn main:app --host 0.0.0.0 --port 10000