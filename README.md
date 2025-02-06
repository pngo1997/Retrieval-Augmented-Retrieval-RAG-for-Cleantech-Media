# 🔍 Retrieval Augmented Generation (RAG) for Cleantech Media  

## 📜 Overview  
This project focuses on implementing a **Retrieval-Augmented Generation (RAG) system** to retrieve and summarize clean technology articles. Using the **Cleantech Media Dataset** from Kaggle, the system processes, stores, and retrieves articles using vector databases and generates responses via **Large Language Models (LLMs)**.  

The project builds upon the **"Cleantech RAG"** tutorial from the **Next-Gen Cleantech Solutions workshop** (SwissText2024). It incorporates **additional enhancements**, including alternative text splitters, embeddings, LLMs, and evaluation techniques.  

## 🚀 1️⃣ System Workflow  

1️⃣ **Vector Database Creation**  
- Preprocess **20,122 articles** from the **Cleantech Media Dataset**.  
- Chunk articles using multiple **text splitters** (RecursiveCharacter, NLTKTextSplitter).  
- Store chunks in a **vector database** using embeddings.  

2️⃣ **Query Processing via RAG Pipeline**  
- User submits a **clean technology-related query**.  
- Retrieve relevant chunks from the **vector database**.  
- Generate an **answer summary** using an **LLM**.  

3️⃣ **Evaluation & Benchmarking**  
- Evaluate retrieval performance using **Cleantech RAG Evaluation Dataset (23 instances)**.  
- Compare different retrieval settings, LLM models, and prompt variations.  
- Use **ROUGE, Perplexity, BERTScore, and RAGAS metrics** for evaluation.  
- Conduct **qualitative analysis** of generated responses.  

## 📊 2️⃣ Dataset  

### **1. Training Dataset**  
📄 **Cleantech Media Dataset** ([Kaggle](https://www.kaggle.com/datasets/anacode/cleantech-media-dataset))  
- **20,122 web articles** on clean technologies.  
- Sources: **pv-magazine, energy-xprt, and more**.  
- Timeframe: **Jan 2022 – Oct 2024**.  
- Used to **build the retrieval system**.  

### **2. Evaluation Dataset**  
📄 **Cleantech RAG Evaluation Dataset**  
- **23 evaluation instances** for RAG performance testing.  
- Used for **retrieval and answer generation assessment**.  

📌 **Parsing Note**:  
- Uses **`;` delimiter** instead of `,` (important for correct parsing).  
- **Columns Used**:  
  - `question` → **User query**  
  - `relevant_text` → **Ground truth for retrieval**  
  - `answer` → **Expected generated response**  

## 🛠 3️⃣ Implementation Details  

### **📌 1. Data Processing & Chunking**  
✅ **Text Splitters Used**:  
- **RecursiveCharacterTextSplitter** (baseline)  
- **NLTKTextSplitter** (linguistically aware)  

📌 **Chunk Configurations**:  
- **(256, 64)**  
- **(1024, 128)**  

✅ **Enhancements**:  
- Added **"in-document chunk ID"** to metadata.  
- Preprocessed text to improve chunk separation.
  
### **📌 2. Embeddings & Vector Database**  
✅ **Embedding Models Used**:  
1️⃣ **"mini"**  
2️⃣ **"bge-m3"**  
3️⃣ **"gte"**  

✅ **Analysis Performed**:  
- **Embedding space distribution**  
- **Similarity statistics**  

### **📌 3. RAG Pipeline Enhancements**  

✅ **New Components Added**:  
- **Alternative RAG prompts** for better chunk retrieval.  
- **Different values for retrieved chunks (k = {1, 3, 5})**.  

✅ **LLMs Used**:  
- **GPT-4-turbo**  

✅ **Evaluation Experiments**:  
- Impact of chunk retrieval count (`k`) on results.  
- Performance comparison of different LLMs.  

### **📌 4. Answer Generation & Evaluation**  

✅ **Additional Prompt Experiments**:  
- Designed alternative `answer_generation_prompt` for better summaries.  

✅ **Metrics Used for Evaluation**:  
1️⃣ **ROUGE** (Lexical overlap)  
2️⃣ **Perplexity** (Fluency measurement)  
3️⃣ **BERTScore** (Semantic similarity)  
4️⃣ **RAGAS** (RAG-specific retrieval evaluation)  

✅ **Qualitative Analysis**:  
- **Manual review of select query responses**.  
- **Comparison between LLM-generated and ground-truth answers**.  

📌 **Optional Enhancements**:  
- **Synthetic Q-A pair generation** (`generate_synthetic_qa_pairs()`).  
- **Advanced RAG techniques**.  

## 📌 5️⃣ Summary  

✅ Implemented RAG pipeline on Cleantech dataset.

✅ Enhanced retrieval using new chunking methods.

✅ Analyzed embedding models & retrieval effectiveness.

✅ Experimented with multiple LLMs & prompt designs.

✅ Evaluated system with ROUGE, Perplexity, BERTScore & RAGA.

✅ Performed qualitative analysis on generated responses.
