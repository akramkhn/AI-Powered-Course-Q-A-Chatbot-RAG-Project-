📌 Overview

This project implements a Retrieval-Augmented Generation (RAG) based chatbot that allows users to ask natural language questions about a web development course and receive accurate answers with exact video numbers and timestamps.

Instead of relying only on an LLM, the system retrieves relevant subtitle content from course videos and uses it as context, ensuring grounded and reliable responses.

------------------------------------------------------------------------------------------------------------------------------------------------------------------

❓ Problem Statement

Online courses often contain long videos, making it time-consuming for learners to locate where a specific topic is explained.

Learners usually:

Scrub through videos manually

Rely on incomplete timestamps

Miss relevant explanations

-------------------------------------------------------------------------------------------------------------------------------------------------------------

✅ Solution

This project solves the problem by:

Converting course videos into timestamped transcripts

Indexing transcript chunks using semantic embeddings

Retrieving the most relevant content using vector similarity search

Generating answers using Retrieval-Augmented Generation (RAG)

The chatbot guides users directly to the exact video and timestamp where a concept is taught.

<img width="1348" height="633" alt="image" src="https://github.com/user-attachments/assets/c80b3c2a-8ece-4359-b1cf-e3ed374b311b" />

--------------------------------------------------------------------------------------------------------------------------------------------------------------

High-level flow:

1) Video → Audio extraction

2) Audio → Timestamped text (Speech-to-Text)

3) Text → Semantic embeddings

4) User query → Similarity search

5) Retrieved context → LLM response

--------------------------------------------------------------------------------------------------------------------------------------------------------------


🔄 Detailed Workflow
1️⃣ Video to Audio Processing

Converts course videos into audio files using FFmpeg

Preserves video metadata (video number and title)

Enables batch processing

📄 File: Videos to Audio.py


--------------------------------------------------------------------------------------------------------------------------------------------------------------

2️⃣ Speech-to-Text Transcription

Uses Whisper (large-v2) for transcription

Translates non-English audio into English

Generates timestamped subtitle chunks

Stores output in structured JSON format

📄 File: creating_chunks.py

--------------------------------------------------------------------------------------------------------------------------------------------------------------


3️⃣ Embedding Generation

Converts each subtitle chunk into a semantic embedding

Embeddings are generated using a local embedding model

Chunk metadata and embeddings are stored together

Acts as a lightweight vector store

📄 File: creating_embedding.py


--------------------------------------------------------------------------------------------------------------------------------------------------------------


4️⃣ Query Processing & Retrieval

Converts user questions into embeddings

Uses cosine similarity to retrieve the most relevant chunks

Selects top matching chunks as context

📄 File: process_incoming.py


--------------------------------------------------------------------------------------------------------------------------------------------------------------

5️⃣ Retrieval-Augmented Generation (RAG)

Injects retrieved subtitle chunks into a structured prompt

Uses an LLM to generate human-friendly, grounded answers

Responds only using course content to avoid hallucinations


--------------------------------------------------------------------------------------------------------------------------------------------------------------



✨ Key Features

📍 Timestamp-level content retrieval

🔍 Semantic search over subtitles

🧠 Retrieval-Augmented Generation (RAG)

🎯 Grounded, course-specific answers

📚 Faster navigation of long-form educational content

--------------------------------------------------------------------------------------------------------------------------------------------------------------

🛠 Technologies Used

Python

FFmpeg

Whisper (Speech-to-Text)

Semantic Embeddings

Vector Similarity Search (Cosine Similarity)

Large Language Models (LLMs)

Pandas, NumPy

Joblib

--------------------------------------------------------------------------------------------------------------------------------------------------------------


🚀 Why This Project Matters

Demonstrates a real-world RAG use case

Focuses on data preparation and retrieval, not just LLM usage

Solves a practical learning problem

Bridges Data Engineering and AI systems


--------------------------------------------------------------------------------------------------------------------------------------------------------------

🔮 Future Improvements

Replace in-memory storage with a vector database

Support incremental updates for new videos

Deploy as a web application

Integrate with cloud platforms (Azure)
