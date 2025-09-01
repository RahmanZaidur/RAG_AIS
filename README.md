# Smart Waterways: A Retrieval-Augmented AI Framework for Vessel Tracking and Decision Support

This project implements a **Retrieval-Augmented Generation (RAG) chatbot** for maritime decision support, leveraging **AIS (Automatic Identification System) vessel tracking data**. The chatbot allows users to ask natural language questions about vessel positions, movements, and characteristics, retrieving information from a structured **AIS CSV dataset**. If no relevant information is found, the system falls back to general maritime knowledge.

Built with **LangChain**, **Gradio**, **HuggingFace embeddings**, and **ChromaDB**, this project provides an intelligent conversational interface for maritime research and operational decision-making.

---

## Features

- **CSV Data Ingestion**  
  Loads AIS data from CSV with vessel attributes (e.g., MMSI, coordinates, speed, vessel type).  

- **Vector Database (ChromaDB)**  
  Embeds vessel records for semantic retrieval and efficient querying.  

- **LLM-Powered Querying**  
  Uses **Groq LLaMA-3.3-70B** as the reasoning engine for natural language queries.  

- **Self-Query Retriever**  
  Automatically translates user questions into structured filters over AIS metadata.  

- **Conversational Memory**  
  Maintains context across queries for multi-turn conversations.  

- **Fallback Mechanism**  
  If no relevant AIS records are found, the chatbot falls back to general maritime knowledge.  

- **Gradio Web Interface**  
  Interactive UI for querying AIS datasets with chat-based visualization.  

---

## Project Structure

```
├── AIS_sampleData2.csv            # Example AIS dataset
├── AIS_sampleData2_db_V2/         # Persisted ChromaDB embeddings
├── app.py                         # Main chatbot application
├── requirements.txt               # Python dependencies
└── README.md                      # Project documentation
```

---

## Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/RahmanZaidur/RAG_AIS.git
cd RAG_AIS
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Environment variables
Set your **Groq API key**:
```bash
export GROQ_API_KEY="your_api_key_here"
```

### 4. Run the application
```bash
python app.py
```

The Gradio interface will launch at:
```
http://127.0.0.1:7860
```

---

## 🛠️ Tech Stack

- **[LangChain](https://www.langchain.com/)** – RAG pipeline & conversational chains  
- **[Chroma](https://www.trychroma.com/)** – Vector database for embeddings  
- **[HuggingFace Embeddings](https://huggingface.co/BAAI/bge-small-en)** – `bge-small-en` model for text embeddings  
- **[Groq LLM](https://groq.com/)** – LLaMA-3.3-70B for reasoning and query understanding  
- **[Gradio](https://gradio.app/)** – Web UI for chatbot interaction  

---

## Example Queries

- *"Where is vessel **Ever Given** currently located?"*  
- *"Show me all vessels traveling above 15 knots."*  
- *"What is the size of the vessel with MMSI 366123456?"*  

If AIS data does not contain relevant info, the chatbot responds with general maritime knowledge.

---

## Key Components

### 1. **CSV Loader**
Loads AIS data with metadata columns (MMSI, VesselName, LAT, LON, etc.).

### 2. **Retriever**
`SelfQueryRetriever` allows LLM to parse natural language into metadata-based queries.

### 3. **Conversational Chain**
Maintains chat history while retrieving AIS records.

### 4. **Fallback Chain**
Provides expert maritime responses when AIS data is insufficient.

### 5. **Gradio UI**
Simple interactive chatbot with input box, history, and clearing options.

---

## 👩‍💻 Authors

- **Zaidur Rahman**  
- **Dr. Heather Nachtmann**  

Presented at **Smart Rivers 2025**  
University of Arkansas  

---

## 📜 License

This project is licensed under the **MIT License** – feel free to use and adapt.  
