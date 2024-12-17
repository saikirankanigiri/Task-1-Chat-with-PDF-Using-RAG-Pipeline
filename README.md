Overview
This project implements a Retrieval-Augmented Generation (RAG) pipeline that enables users to interact with semi-structured data from multiple PDF files. The system extracts, chunks, embeds, and stores data for efficient similarity-based retrieval. It answers user queries and performs comparisons accurately using a custom response generation method without relying on external LLMs.

Functional Features
Data Ingestion

Input: Upload PDF files containing semi-structured data.
Process:
Extract text and structured information from PDFs.
Split data into logical chunks for better granularity.
Convert text chunks into vector embeddings using Sentence Transformers.
Store embeddings in a vector database (e.g., FAISS) for efficient retrieval.
Query Handling

Input: User's natural language queries.
Process:
Convert queries into vector embeddings using the same embedding model.
Perform similarity search in the vector database to fetch the most relevant data chunks.
Generate responses using custom logic or locally hosted models.
Comparison Queries

Input: User query requesting comparisons.
Process:
Identify the relevant fields or terms for comparison.
Retrieve corresponding chunks from the database.
Process and aggregate the data into structured formats like tables.
Response Generation

Input: Retrieved chunks of relevant data and the user query.
Process:
Use the retrieved information to generate factual responses.
Responses are structured and directly reflect the extracted data.
How It Works
1. Upload PDFs
Use the web interface to upload PDF files for processing.
2. Ask Queries
Input natural language queries to retrieve accurate answers.
3. Ask for Comparisons
Use queries like Compare the official languages of Andhra Pradesh and Assam to get tabular comparisons.
4. Access Application
Run the backend and visit http://localhost:5000 in your browser to access the UI.
Directory Structure
plaintext
Copy code
Chat-With-PDF-RAG/
│
├── data/                # Directory for PDF uploads
├── embeddings/          # Storage for vector embeddings
├── app.py               # Main backend application (Flask/FastAPI)
├── queryHandler.js      # Frontend logic for handling queries
├── templates/           # Frontend UI files
│   └── index.html       # HTML UI for user interaction
├── requirements.txt     # Python dependencies
└── README.md            # Project documentation
API Endpoints
Endpoint	Method	Description
/upload	POST	Uploads and processes a PDF file.
/ask	POST	Handles user queries and retrieves data.
/compare	POST	Processes comparison-related queries.
Example Queries
Simple Query
Input:

plaintext
Copy code
What is the capital of Andhra Pradesh?
Response:

json
Copy code
{
  "State": "Andhra Pradesh",
  "Capital": "Amaravati"
}
Comparison Query
Input:

plaintext
Copy code
Compare the official languages of Andhra Pradesh and Assam.
Response:

State	Official Language	Additional Language
Andhra Pradesh	Telugu	Urdu
Assam	Assamese	None
Technology Stack
Component	Tool/Library
Backend	Python, Flask/FastAPI
PDF Processing	PyPDF2, pdfminer.six
Text Embeddings	Sentence Transformers
Vector Database	FAISS
Frontend	HTML, CSS, JavaScript
Response Generation	Custom logic or locally hosted models
Future Enhancements
Planned Feature	Description
Parallel PDF Processing	Support large-scale PDFs with faster performance.
Advanced Comparison Visuals	Add charts and graphs for better visual comparisons.
Multilingual Support	Handle PDFs and queries in multiple languages.
Hybrid Search Optimization	Combine keyword-based and vector-based retrieval.
Setup Instructions
Clone the Repository

bash
Copy code
git clone https://github.com/your-username/Chat-With-PDF-RAG.git
cd Chat-With-PDF-RAG
Install Dependencies

bash
Copy code
pip install -r requirements.txt
Run the Backend

bash
Copy code
python app.py
Access the Application Open http://localhost:5000 in your browser.

Contributing
Contributions are welcome! Follow these steps to contribute:

Fork the repository.
Create a new branch:
bash
Copy code
git checkout -b feature-branch
Commit your changes:
bash
Copy code
git commit -m "Add new feature"
Push to your branch and submit a pull request.
License
This project is licensed under the MIT License. See the LICENSE file for details.

Acknowledgments
Tool/Library	Purpose
Hugging Face	Pre-trained embeddings (Sentence Transformers).
FAISS	Vector search capabilities.
PyPDF2 / pdfminer.six	PDF text extraction.
