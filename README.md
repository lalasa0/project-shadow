Project SHADOW - Retrieval-Augmented Generation (RAG) for Intelligence Retrieval
Overview
This project implements a Retrieval-Augmented Generation (RAG) system designed to simulate a real-world intelligence retrieval assistant. The system retrieves relevant classified information based on an agent's query and clearance level. It combines vector embeddings and graph-based retrieval to generate responses from two key knowledge sources:

Secret Info Manual: Contains highly classified intelligence data.

Response Framework: Provides response protocols based on agent level and query type.

Key Features:
Retrieval Mechanism: Utilizes vector similarity (via embeddings) and graph-based retrieval to fetch the most relevant information.

Security Protocols: Ensures agents can only access information within their clearance level, enforcing strict access control.

Dynamic Responses: Generates agent-specific responses based on clearance level, ranging from basic to cryptic strategies.

Modular Design: The system is scalable to support new protocols, data sources, or retrieval mechanisms.

Technologies Used
Python 3

FAISS: For fast vector-based search.

Sentence Transformers: For embedding text chunks.

NetworkX: For graph-based retrieval.

python-docx: For reading .docx files (Secret Info Manual and Response Framework).

Setup and Installation
1. Clone the Repository:
To get started, clone the repository and navigate into the project folder:

bash
Copy
Edit
git clone <repository-url>
cd project-shadow
2. Install Dependencies:
Create a virtual environment and install the required packages:

bash
Copy
Edit
pip install -r requirements.txt
3. Run the Jupyter Notebook:
Open the notebook shadow_retriever.ipynb in Jupyter:

bash
Copy
Edit
jupyter notebook shadow_retriever.ipynb
4. Query the System:
Select an agent level (Level 1 to Level 5).

Input a classified query.

The system will retrieve relevant information and generate a response based on the agent’s clearance level.

File Structure
plaintext
Copy
Edit
project-shadow/
├── README.md                  <- This file (project overview and instructions)
├── shadow_retriever.ipynb     <- Jupyter notebook containing the code and test cases
├── data/
│   ├── SECRET INFO MANUAL.docx  <- Secret information document (classified data)
│   └── RAG CASE RESPONSE FRAMEWORK.docx <- Response framework for query generation
└── requirements.txt           <- List of required Python dependencies
Explanation of the System
The system is built around the Retrieval-Augmented Generation (RAG) model. Here's how it works:

1. Document Chunking:
The documents (SECRET INFO MANUAL and RAG CASE RESPONSE FRAMEWORK) are split into manageable chunks to ensure fast and relevant retrieval.

2. Vector Embeddings:
Text chunks are converted into embeddings using Sentence Transformers. These embeddings are stored in FAISS for efficient similarity-based search.

3. Security Handling:
The system checks the agent’s clearance level before allowing access to sensitive data. If an agent's clearance level is insufficient, the system returns:

"Access Denied - Clearance Insufficient."

4. Response Generation:
Based on the retrieved data, the system generates responses that vary according to the agent’s clearance level:

Level 1 agents receive basic, instructional responses.

Level 5 agents get cryptic, high-level strategic advice.

Security Protocols
Clearance Level Check: Ensures agents only access information they are authorized to view.

Sensitive Data Retrieval: Restricts access to level 7 or higher data, which is only accessible by agents with the appropriate clearance.

Access Control: If a query doesn’t match any available data, the system returns:

"Oops !! No matching data found."

Future Improvements
Advanced Chunking & Storage: Optimizing the document chunking process for better performance with larger datasets.

Modular Pipeline: Expanding the system to handle additional knowledge sources and security protocols.

