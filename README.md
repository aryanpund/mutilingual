# Multilingual PDF Document Analysis

## Overview
This project extracts text from PDFs, processes the extracted text, generates embeddings using Sentence Transformers, and stores them in a FAISS vector database for efficient retrieval. It then utilizes the Ollama language model to generate responses to user queries based on the stored text.

## Features
- Extract text from PDFs using `PyMuPDF` (`fitz`) and `pytesseract` (for OCR-based extraction).
- Clean and preprocess the extracted text.
- Chunk text using `RecursiveCharacterTextSplitter` for efficient vector storage.
- Generate text embeddings using `SentenceTransformer`.
- Store and retrieve text chunks using `FAISS` for efficient similarity search.
- Generate responses to queries using `Ollama`'s `llama3.2` model.

## Installation
### Prerequisites
Ensure you have the following installed:
- Python 3.8+
- Pip

### Install Required Packages
Run the following command to install dependencies:
```sh
pip install pymupdf pytesseract pillow langchain sentence-transformers faiss-cpu numpy ollama
```

## Usage
1. **Extract Text from a PDF**
   - Place your PDF file in the appropriate directory.
   - Update the `pdf_path` variable in `main.py` with the correct path.

2. **Run the Script**
   ```sh
   python main.py
   ```

3. **Query Processing**
   - The script will process predefined queries and fetch relevant chunks from FAISS.
   - Ollama's model will generate structured responses.

## How It Works
1. **Text Extraction:** The script extracts text from a given PDF, either through direct text extraction or OCR if the text is embedded in images.
2. **Text Cleaning & Chunking:** The extracted text is cleaned to remove noise and special characters, then split into manageable chunks to facilitate efficient storage and retrieval.
3. **Embedding Generation:** Each text chunk is converted into an embedding vector using a pre-trained Sentence Transformer model.
4. **Vector Storage:** The embeddings are stored in a FAISS vector database for fast similarity searches.
5. **Query Handling:** When a query is input, it is also converted into an embedding, and the closest matching text chunks are retrieved.
6. **Response Generation:** The retrieved text chunks are provided as context to Ollama's language model, which generates a well-structured response.

## Example Output
```
Query: Summarize the document's key themes, major ideas, and underlying messages in detail.
Generated Response:
- Theme 1: Leadership Principles...
- Theme 2: Decision-Making Strategies...
- Theme 3: Cultural Impact of Leadership...
```

## Future Enhancements
- Support for multiple languages in OCR processing.
- Integration with a web interface for interactive querying.
- Optimization for large-scale document processing.

## License
This project is licensed under the MIT License.

## Author
Aryan Pund

