Chat with PDF using RAG Pipeline
Overview
This project implements a Retrieval-Augmented Generation (RAG) pipeline to allow users to interact with semi-structured data from PDF files. The system extracts, chunks, embeds, and stores data for efficient retrieval. It answers user queries and performs comparisons using custom logic and embeddings without relying on external LLMs.

Functional Features
1. Data Ingestion
Input: PDF files containing semi-structured data.
Process:
Extract text and structured data from PDFs.
Split data into logical chunks.
Convert text chunks into vector embeddings using Sentence Transformers.
Store embeddings in a vector database (e.g., FAISS).
2. Query Handling
Input: Natural language queries from users.
Process:
Convert user queries into vector embeddings.
Perform a similarity search in the vector database.
Fetch relevant data chunks for further processing.
3. Comparison Queries
Input: Queries requesting comparisons.
Process:
Identify fields or terms to compare.
Retrieve corresponding chunks from the vector database.
Aggregate and structure data for comparisons (e.g., in tables).
4. Response Generation
Input: Retrieved data chunks and user query.
Process:
Use custom logic to generate factual responses.
Ensure responses are structured and contextually accurate.
How It Works
Step 1: Upload PDFs
Upload the PDFs through the web interface for processing.

Step 2: Ask Queries
Ask natural language questions to retrieve relevant answers.

Step 3: Comparison Queries
Use queries like Compare the official languages of Andhra Pradesh and Assam to get comparative outputs.

Step 4: Access the Application
Run the backend server and access the application at http://localhost:5000.

Directory Structure
plaintext
Copy code
Chat-With-PDF-RAG/
│
├── data/                # Directory for PDF uploads
├── embeddings/          # Storage for vector embeddings
├── app.py               # Main backend application (Flask/FastAPI)
├── queryHandler.js      # Frontend query handling logic
├── templates/           # Frontend UI files
│   └── index.html       # HTML file for user interface
├── requirements.txt     # Python dependencies
└── README.md            # Project documentation
API Endpoints
Endpoint	Method	Description
/upload	POST	Upload and process a PDF file.
/ask	POST	Retrieve data based on user queries.
/compare	POST	Process and retrieve comparison data.
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
Response Generation	Custom logic
Future Enhancements
Feature	Description
Parallel PDF Processing	Support faster and large-scale PDF processing.
Advanced Comparison Visuals	Add visualizations like charts and graphs.
Multilingual Support	Enable support for PDFs in multiple languages.
Hybrid Search Optimization	Combine keyword and vector-based retrieval.
Setup Instructions
1. Clone the Repository
bash
Copy code
git clone https://github.com/your-username/Chat-With-PDF-RAG.git
cd Chat-With-PDF-RAG
2. Install Dependencies
bash
Copy code
pip install -r requirements.txt
3. Run the Backend
bash
Copy code
python app.py
4. Access the Application
Open your browser and navigate to http://localhost:5000.

Contributing
We welcome contributions! Follow these steps to contribute:

Fork the repository.
Create a new branch:
bash
Copy code
git checkout -b feature-branch
Commit your changes:
bash
Copy code
git commit -m "Add new feature"
Push the branch:
bash
Copy code
git push origin feature-branch
Submit a pull request for review.
License
This project is licensed under the MIT License. See the LICENSE file for more details.

Acknowledgments
Tool/Library	Purpose
Hugging Face	Pre-trained embeddings (Sentence Transformers).
FAISS	Efficient vector search capabilities.
PyPDF2 / pdfminer.six	PDF text extraction libraries.
