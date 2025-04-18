# Project SHADOW - Retrieval-Augmented Generation (RAG) for Intelligence Retrieval

## Overview  
Project SHADOW is a simulation of a real-world intelligence retrieval assistant powered by **Retrieval-Augmented Generation (RAG)**. The system processes queries from agents, retrieves relevant classified information based on clearance level, and generates structured, level-specific responses using hybrid retrieval methods.

## Knowledge Sources  
- **Secret Info Manual**: Contains classified intelligence data  
- **Response Framework**: Defines how responses should be constructed for each agent level and query type

## Key Features  
- **Retrieval Mechanism**: Combines vector similarity (via embeddings) and graph-based traversal  
- **Security Protocols**: Enforces agent-level clearance restrictions  
- **Dynamic Response Generation**: Custom responses based on agent identity and intent  
- **Fail-safe Responses**: Returns fallback message if no relevant data is found or access is denied

## Technologies Used  
- Python 3  
- FAISS (vector search engine)  
- Sentence Transformers (text embedding)  
- NetworkX (graph traversal)  
- python-docx (reading `.docx` intelligence files)

## System Flow  

1. **Document Chunking**  
   - Splits `.docx` files into ~500-character chunks  
   - Prepares for semantic search using embeddings

2. **Embedding & Retrieval**  
   - Converts text chunks into dense vectors  
   - Uses FAISS for fast nearest-neighbor search  
   - Supports hybrid logic for complex, multi-hop queries

3. **Security Handling**  
   - Agents must select their level (1–5)  
   - If they attempt to access restricted content (Level 7+), the system responds with:  
     ```
     Access Denied - Clearance Insufficient.
     ```

4. **Response Generation**  
   - Agent Level 1: Instructional guidance  
   - Agent Level 5: Strategic, cryptic summaries  
   - No matching data:  
     ```
     Oops !! No matching data found.
     ```

## File Structure  
```plaintext
project-shadow/
├── README.md
├── shadow_retriever.ipynb       ← Notebook containing full logic and demo
├── requirements.txt             ← Required dependencies
├── data/
│   ├── SECRET INFO MANUAL.docx
│   └── RAG CASE RESPONSE FRAMEWORK.docx

```
Setup Instructions
**Step 1: Clone the Repository**
``` git clone <git clone https://github.com/lalasa0/project-shadow.git>
cd project-shadow
```
**Step 2: Install Dependencies**
```
pip install -r requirements.txt
```
**Step 3: Run the Notebook**
```
jupyter notebook shadow_retriever.ipynb
```
**Step 4: Query the System**
Select an agent level (Level 1 to Level 5)

Enter your query

Review the generated response with relevant retrieved context

**Example Responses**
Level 3 Query → Counter-surveillance protocols for “Operation Eclipse”
→ Returns RED-FLAG protocols and strategic response rules

Level 1 Query → Disguise techniques
→ Returns simplified concealment instructions

Level 3 Query on Level 7 Content
→

```
Access Denied - Clearance Insufficient.
```
