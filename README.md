🏥 Medical Chatbot with RAG (FAISS + Hugging Face)

This project is a Retrieval-Augmented Generation (RAG) based Medical Chatbot.
It allows users to ask questions related to medical PDFs, and the chatbot answers strictly based on the uploaded documents, using vector search and a Hugging Face LLM.

 🚀 Features

 📄 Load and process medical PDF documents
 ✂️ Split documents into chunks
 🧠 Generate embeddings using Sentence Transformers
 📦 Store and retrieve vectors using FAISS
 🤖 Generate answers using Hugging Face Inference API
 🔍 Context-aware answers (no hallucination)
 ❌ Says “I don’t know” if the answer is not in the documents

 🛠 Tech Stack
 Python 3.10+
 LangChain
 FAISS
 Hugging Face Inference API
 Sentence-Transformers
 Transformers
 Dotenv

 📁 Project Structure
medical-chatbot-main/
│
├── data/
│   └── .pdf                   Medical PDF files
│
├── vectorstore/
│   └── db_faiss/               FAISS index (auto-created)
│
├── create_memory_llm.py        Build FAISS vector database
├── connect_memory_with_llm.py  Query chatbot
│
├── .env                        Hugging Face token
├── requirements.txt
└── README.md

 🔑 Environment Setup
 1️⃣ Create .env file
HF_TOKEN=your_huggingface_api_token_here
> Make sure your token has Inference API access.

 📦 Install Compatible Dependencies (IMPORTANT)
Use exact versions to avoid errors:

bash
pip install --force-reinstall \
  huggingface-hub==0.22.2 \
  transformers==4.38.0 \
  sentence-transformers==2.6.1 \
  langchain==0.1.15 \
  langchain-community==0.0.28 \
  langchain-huggingface==0.0.7 \
  faiss-cpu \
  python-dotenv




 ⚙️ Step-by-Step Usage

 ✅ Step 1: Build Vector Database
Add your medical PDFs inside the data/ folder, then run:

bash
python create_memory_llm.py

✔ This will:
 Load PDFs
 Split into chunks
 Generate embeddings
 Store them in FAISS (vectorstore/db_faiss)

 ✅ Step 2: Run the Chatbot
bash
python connect_memory_with_llm.py
Example:
Write Query Here: What are the symptoms of diabetes?
 🧠 How It Works (RAG Pipeline)

1. User enters a query
2. FAISS retrieves top-K relevant chunks
3. Context + question are merged into a prompt
4. Hugging Face LLM generates the answer
5. Sources are displayed



 ⚠️ Important Notes

 The chatbot does NOT use the internet
 Answers are strictly based on PDFs
 Prevents hallucinations by design
 Uses manual RAG to ensure compatibility with older LangChain versions

 🧪 Common Issues & Fixes
 ❌ ValidationError: temperature in model_kwargs
✔ Fixed by passing temperature explicitly to HuggingFaceEndpoint

 ❌ InferenceClient has no attribute post
✔ Fixed by using compatible huggingface-hub version

 ❌ sentence-transformers import error
✔ Fixed by downgrading huggingface-hub < 1.0

 📌 Future Improvements
 Streamlit UI
 User authentication
 Multi-PDF upload
 Medical image diagnosis
 Doctor recommendation system

 👨‍💻 Author
Karan Kumar Ghosh
Bitan Bannerjee
Souhardya Nandy
Deeptangshu Sen
Suvajit Biswas
B.Tech CSE-IOT
Medical AI & Generative AI Projects


