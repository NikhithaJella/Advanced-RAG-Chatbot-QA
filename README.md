Advanced RAG QA Chatbot with LangChain
Welcome to the Advanced RAG (Retrieval-Augmented Generation) QA Chatbot project! This repository contains a practical implementation of a system that can "read" a technical PDF—in this case, the seminal "Attention Is All You Need" paper—and answer complex questions about it using Google’s Gemini model.


🚀 Overview
The core of this project is a RAG pipeline. Instead of relying on a LLM's static training data, we provide it with specific context from a document. This reduces hallucinations and allows for highly accurate, domain-specific conversations.

How it works:
1. Ingestion: We load the attention.pdf using PyPDFLoader.
2. Chunking: The text is broken down into 1000-character pieces with a 200-character overlap to ensure no context is lost at the edges.
3. Embedding: We use HuggingFaceInstructEmbeddings to convert text into numerical vectors.
4. Vector Store: These vectors are stored in a FAISS (Facebook AI Similarity Search) index for lightning-fast retrieval.
5. Generation: When you ask a question, the system finds the most relevant chunks and feeds them to the Gemini-2.5-Flash model via LangChain to generate a grounded response.

🛠️ The Tech Stack
Framework: LangChain (Core, Community, and Google GenAI)
LLM: Google Gemini 2.5 Flash
Vector Database: FAISS
Embeddings: Instructor-Large (HuggingFace)
Environment: Python 3.x, Jupyter Notebook

📁 Project Structure

```text
.
├── data/
│   └── attention.pdf          # The research paper used as context
├── retriever_and_chain.ipynb  # Main logic and LangChain implementation
├── requirements.txt           # Python dependencies
└── README.md                  # You are here!


⚙️ Setup & Installation
1. Clone the repo:
                git clone <your-repo-link>
                cd RAG_QA_Chatbot

2. Install Dependencies:It's recommended to use a virtual environment.
                pip install -r requirements.txt

3. Set up your API Key:You'll need a Google Gemini API key. The notebook uses getpass to securely prompt you for the key during execution.

4. Run the Notebook:Open retriever_and_chain.ipynb in VS Code or Jupyter and run the cells sequentially.


🤖 Key Features
1. Step-by-Step Reasoning: The prompt template is engineered to make the LLM "think" before answering, improving the quality of technical explanations.
2. Instructional Embeddings: Uses high-quality embeddings that are optimized for retrieval tasks.
3. Visualizations: The project is tested against the "Attention Is All You Need" paper, so it's ready to handle queries about Scaled Dot-Product Attention, Multi-Head Attention, and Positional Encodings.

📝 Example Query

Input: "How does Scaled Dot-Product Attention work?"
Output: The model retrieves specific math from page 4 of the PDF, explains the dot-product operation, the $\sqrt{d_k}$ scaling factor, and the final Softmax application—all based only on the provided text.


Happy Coding! If you find this helpful, feel free to drop a star!