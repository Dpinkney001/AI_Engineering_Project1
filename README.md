# AI_Engineering_Project1
In this project, you'll build The Unofficial Guide: a RAG (Retrieval-Augmented Generation) system that makes this kind of student-generated knowledge searchable and answerable. A user asks a plain-language question — "Is the housing lottery actually random?" or "Which CS professor gives the most useful feedback?" — and gets a grounded, cited answer drawn from real documents you collected.

This is your first production AI project. More structure is provided here than in later projects — use it to build the habits (spec first, evaluate honestly, document completely) that you'll need when that structure is gone.

🎯 Goals
By completing this project, you will be able to:

Build an end-to-end document processing pipeline: ingestion, chunking, and embedding.
Set up and query a vector store for semantic search.
Generate grounded responses using retrieved context.
Design and run an evaluation framework to measure how well your system actually works.
Document your design decisions so someone else could understand and extend your system.

✅ Features
Required Features

Document Ingestion Pipeline: Collect and process at least 10 documents from your chosen domain. Your pipeline must: load the raw documents, clean or preprocess them as needed (remove navigation text, ads, etc.), and produce structured text ready for chunking. Describe this process in your README.


Chunking Strategy: Split your documents into chunks using a deliberate strategy — not just "split every 500 characters." Your planning.md must explain your chunk size, overlap, and why those choices fit your documents. For example, review-style text may warrant smaller chunks than long-form guides.


Vector Store and Semantic Search: Embed your chunks and store them in a vector database. Given a user query, retrieve the top relevant chunks using semantic similarity search. Your README should name the embedding model you used and reflect on what tradeoffs you'd consider if you were choosing for a production system (cost, context length, multilingual support, local vs. API).


Grounded Response Generation: Use an LLM to generate an answer to the user's query using only the retrieved chunks as context. Responses should not rely on the model's general knowledge — they should be grounded in what was retrieved. Include source attribution (which document(s) the answer draws from) in every response.


Query Interface: Build a basic interface for querying your system. This can be a simple web UI, a command-line tool, or a notebook — but it must be usable enough to demonstrate in your video without explaining how to navigate it.


Evaluation Report: Design 5 test questions with ground-truth answers, then run your system on each and evaluate the results. For each question, your report should document: the question, the correct answer, what your system returned, which chunks were retrieved, and whether the retrieval and response were accurate, partially accurate, or inaccurate. Identify at least one failure case and explain why it happened.

Stretch Features
Complete any of these for extra credit. Update your planning.md before starting each one.


Hybrid Search: Combine semantic search with keyword (BM25) search and compare results to semantic-only.


Chunking Strategy Comparison: Test 2+ chunking approaches on the same query set and report which performed better and why.


Metadata Filtering: Allow users to filter by document source, date, or rating (e.g., only show reviews from the past year).


Conversational Memory: Support multi-turn queries where the system remembers context from the previous question.

