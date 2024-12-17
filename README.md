# Task-1-Chat-with-PDF-Using-RAG-Pipeline

## Overview

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline to allow users to interact with semi-structured data in multiple PDF files. The system extracts, chunks, embeds, and stores data efficiently for similarity-based retrieval. It answers user queries and performs accurate comparisons leveraging a selected **Large Language Model (LLM)**.

---

## Features

1. **Data Ingestion**
   - Extracts text and relevant structured data from PDF files.
   - Segments the extracted text into logical chunks.
   - Converts chunks into vector embeddings using a pre-trained embedding model.
   - Stores the embeddings in a vector database for efficient retrieval.

2. **Query Handling**
   - Processes user questions and converts them into vector embeddings.
   - Performs similarity search to retrieve the most relevant data chunks.
   - Passes the retrieved data to an LLM to generate accurate responses.

3. **Comparison Queries**
   - Identifies and compares specific terms or fields across multiple PDF files.
   - Aggregates and structures the retrieved data for comparison.
   - Generates responses in structured formats such as tables or bullet points.

4. **Response Generation**
   - Utilizes retrieval-augmented prompts to ensure contextual and factual responses.
   - Ensures accuracy by directly incorporating data retrieved from the vector database.

---

## Functional Workflow

1. **Data Ingestion**
   - Input: PDF files uploaded by the user.
   - Tools: 
     - PDF text extraction library (e.g., PyPDF2, PDFMiner).
     - Pre-trained embedding model (e.g., OpenAI's `text-embedding-ada` or Sentence Transformers).
     - Vector database (e.g., FAISS, Pinecone, or ChromaDB).
   - Output: Vector embeddings stored for retrieval.

2. **Query Handling**
   - Converts user queries into vector embeddings.
   - Performs similarity searches in the vector database to retrieve chunks.
   - Passes retrieved content to the LLM for detailed answers.

3. **Comparison Queries**
   - Detects comparison-related queries.
   - Retrieves corresponding chunks across PDF files.
   - Aggregates and compares the data.
   - Returns responses in tabular or structured format.

4. **Response Generation**
   - LLM generates a final response using the retrieved content and query context.
   - Ensures factual accuracy and completeness.

---

## Project Setup

### Prerequisites

1. **Python** (>=3.8)
2. Libraries:
   - `PyPDF2` or `pdfminer.six` (PDF extraction)
   - `sentence-transformers` (Embeddings)
   - `FAISS` or `Pinecone` (Vector database)
   - `openai` (LLM integration)
   - `Flask` or `FastAPI` (API development)

3. **API Keys**:
   - OpenAI API Key (for embedding model and LLM).

---

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Chat-With-PDF-RAG.git
   cd Chat-With-PDF-RAG
Install dependencies:

bash
Copy code
pip install -r requirements.txt
Set up API keys in your environment:

bash
Copy code
export OPENAI_API_KEY="your_openai_api_key"
How to Run
Start the Backend Server:

Run the following command:
bash
Copy code
python app.py
Upload PDFs:

Use the provided form interface to upload PDFs.
PDFs will be processed, chunked, embedded, and stored in the vector database.
Ask Queries:

Input natural language queries into the query form.
The system will process the query, retrieve relevant data, and generate accurate responses.
Comparison Queries:

Ask questions like: "Compare the Chief Ministers across all states."
The system will identify terms, retrieve relevant chunks, and provide structured comparisons.
Access the system via:

bash
Copy code
http://localhost:5000
Directory Structure
bash
Copy code
Chat-With-PDF-RAG/
│
├── data/                     # Directory to store uploaded PDFs
├── embeddings/               # Directory to store embeddings (if local)
├── app.py                    # Main Flask/FastAPI backend
├── queryHandler.js           # Frontend JS for query handling
├── templates/
│   └── index.html            # Frontend UI for user interaction
├── requirements.txt          # Python dependencies
└── README.md                 # Project Documentation
API Endpoints
Endpoint	Method	Description
/upload	POST	Upload and process a new PDF file.
/ask	POST	Process user queries and return answers.
/compare	POST	Handle comparison-related queries.
Example Queries
Simple Query:

"What is the capital of Andhra Pradesh?"
Response: "The capital of Andhra Pradesh is Amaravati."
Comparison Query:

"Compare the official languages of Andhra Pradesh and Assam."
Response:
sql
Copy code
State              | Official Language      | Additional Language
-------------------------------------------------------------
Andhra Pradesh     | Telugu                 | Urdu
Assam              | Assamese               | None
Technology Stack
Backend: Python, Flask/FastAPI
Frontend: HTML, CSS, JavaScript (Bootstrap for styling)
Embedding Model: Sentence Transformers or OpenAI Embeddings
Vector Database: FAISS or Pinecone
LLM: OpenAI GPT (or any compatible LLM)
Future Enhancements
Add support for large-scale PDFs with parallel processing.
Incorporate advanced comparison charts or visualizations.
Support multilingual PDFs and queries.
Optimize retrieval performance with hybrid search techniques.
Contributing
Contributions are welcome! Please fork this repository and submit pull requests for any improvements or bug fixes.

License
This project is licensed under the MIT License.

Acknowledgments
OpenAI for the LLM and embedding models.
Hugging Face for Sentence Transformers.
FAISS/Pinecone for vector search capabilities.
yaml
Copy code
