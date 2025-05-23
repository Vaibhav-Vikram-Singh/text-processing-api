# Text Processing Backend with FastAPI and Hugging Face Transformers

## Overview

This is a simple backend application built with **FastAPI** that processes text using pre-trained large language models (LLMs) from Hugging Face.  
It supports three tasks:

- **Summarization** of input text  
- **Sentiment analysis**  
- **Keyword / Named Entity Extraction**  

The app exposes RESTful API endpoints to perform these tasks and stores a history of processed requests in memory.

---

## Features

- REST API with two endpoints:
  - `POST /process` — Process input text based on the selected task.
  - `GET /history` — Retrieve history of all processed text requests.
- Uses specific pre-trained Hugging Face models for each task.
- In-memory storage of processed results (no database required).
- Basic input validation and error handling.

---

## Requirements

- Python 3.7 or higher
- FastAPI
- Uvicorn
- Transformers (Hugging Face)
- Nest Asyncio (for running in Jupyter if needed)

---

## Installation

1. Clone this repository:

```bash
git clone <your-repo-url>
cd <repo-folder>


2. Create and activate a virtual environment (optional but recommended):

python -m venv venv
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate


3. Install dependencies:

pip install fastapi uvicorn transformers nest_asyncio




Running the Application

Run the FastAPI app using Uvicorn:

uvicorn main:app --reload

-The server will start at: http://127.0.0.1:8000

-The --reload option enables auto-reload on code changes (development only).



API Endpoints

POST /process

Process input text based on a specified task.

Request JSON Body:

{
  "text": "Your input text here",
  "task": "summarize"  // options: "summarize", "sentiment", "keywords"
}



Response:

{
  "task": "summarize",
  "result": "Summarized text here"
}


Example tasks and results:

"summarize" — returns summarized text.

"sentiment" — returns sentiment label and score.

"keywords" — returns a list of keywords/entities.



GET /history

Returns all processed text requests and their results.

Response:

{
  "history": [
    {
      "text": "Input text",
      "task": "summarize",
      "result": "Summary text"
    }
  ]
}




Notes:

This project uses CPU by default. For GPU acceleration, configure the Transformers pipelines accordingly.

In-memory storage means history will be lost when the server restarts.




