
# 📝 RAG Assignment – Legal Documents Project

This project is an attempt to build a **Retrieval-Augmented Generation (RAG)** pipeline for **legal document analysis**.  
The notebook shows how to preprocess, chunk, embed, and store legal text data for downstream search and question-answering.

---

## 📂 Project Overview

1. **Load Data**
   - The project expects a folder named `corpus/` with sub-folders for different legal datasets:
     ```
     corpus/
       ├─ contractnli/
       ├─ cuad/
       ├─ maud/
       └─ privacy_qa/
     ```
   - Each sub-folder contains plain `.txt` files of legal documents.

2. **Pre-processing**
   - Cleaned raw text (removed emails, phone numbers, special symbols, and stopwords).
   - Calculated basic stats like document lengths and word frequencies.

3. **Chunking**
   - Used `RecursiveCharacterTextSplitter` from LangChain to split each document into **chunks** for easier embedding.
   - Default chunk size: **1000 characters** with **200 character overlap**.

4. **Exploratory Analysis**
   - Computed TF-IDF vectors for sample documents.
   - Measured **cosine similarity** to find similar document pairs.
   - Visualized similarity scores using **Seaborn heatmaps**.

5. **Vector Database**
   - Planned to embed all chunks and store them in a **Chroma vector database** for retrieval during RAG queries.
   - Embeddings were supposed to use **OpenAI’s `text-embedding-3-small` / `text-embedding-3-large` models**.

---

## 🚧 Current Status

The pipeline is **only half complete**:

- ✅ **Data loading, cleaning, chunking, stats, TF-IDF similarity** are done.  
- ❌ **Embedding step stopped midway** because I do not currently have funds to use the OpenAI API for generating embeddings.  
- The last successful step: **created all document chunks** and prepared them for embedding.

---

## 🛠️ Tech Stack

- **Python** (Jupyter Notebook)
- **LangChain** for text splitting and document handling
- **NLTK** for stopwords and text cleaning
- **scikit-learn** for TF-IDF & cosine similarity
- **Seaborn / Matplotlib** for visualization
- **Chroma** for vector database (planned, not fully set up)
- (Planned) **OpenAI Embeddings API** for converting chunks into vectors

---

## ▶️ How to Run (Partial Workflow)

1. Place your datasets inside the `corpus/` folder (as described above).
2. Open the notebook:  
   ```bash
   jupyter notebook RAG_Assg_Legal_Documents_Project.ipynb
   ```
3. Run each cell in order until the **vector embedding** section.
4. For TF-IDF similarity visualizations:
   - Choose either the **first 10 documents** or **10 random documents** to generate similarity heatmaps.

---

## ⚠️ Limitations

- The project currently cannot **store or query embeddings** because the OpenAI API quota is exceeded.
- RAG-based question answering is **not yet implemented** — it will be added after embedding and retrieval steps are completed.

