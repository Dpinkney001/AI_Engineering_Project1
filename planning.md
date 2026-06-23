# Project 1 Planning: The Unofficial Guide

> Write this document before you write any pipeline code.
> Your spec and architecture diagram are what you'll use to direct AI tools (Claude, Copilot, etc.) to generate your implementation — the more specific they are, the more useful the generated code will be.
> Update the Retrieval Approach and Chunking Strategy sections if you change your approach during implementation.
> Update this file before starting any stretch features.

---

## Domain

<!-- What domain did you choose? Why is this knowledge valuable and hard to find through official channels? -->
The domain I choose was cyber security. Cyber Security is a very vast topic and field
and there are many resources that are constantly changing with the technology.
---

## Documents

<!-- List your specific sources: URLs, subreddit names, forum threads, or file descriptions.
     Aim for at least 10 sources that together cover different subtopics or perspectives within your domain. -->

| # | Source      | Description                                  | URL or location |
|---|-------------|----------------------------------------------|-----------------|
| 1 | Black Hat Go                 |Go for programming for hackers and pentesters |AI_Engineering_Project1\documents|
| 2 | Linux basics for hackers     |networking,scripting and security in kali |AI_Engineering_Project1\documents |
| 3 | Malware Data Science        |attack detection and Attribution |AI_Engineering_Project1\documents |
| 4 | penetration testing          |a hands-on introduction to hacking |AI_Engineering_Project1\documents |
| 5 | practical packet analysis   |using wireshark to solve real-world network problems |AI_Engineering_Project1\documents |
| 6 | practical binary analysis    |build your own linux tools for binary instrumention, analysis, and dissembly |AI_Engineering_Project1\documents |
| 7 | Serious Cryptography |a practical introduction to modern encryption |AI_Engineering_Project1\documents |
| 8 | Web security for Developers | real threats, practical defense|AI_Engineering_Project1\documents |
| 9 | Real world bug hunting | a field guide to web hacking | AI_Engineering_Project1\documents |
| 10 | The Car hacker's Handbook | A guide for the Penetration Tester | AI_Engineering_Project1\documents |

---

## Chunking Strategy

<!-- How will you split documents into chunks?
     State your chunk size (in tokens or characters), overlap size, and explain why those
     numbers fit the structure of your documents.
     A review-heavy corpus warrants different chunking than a long FAQ. -->

**Chunk size: **450

**Overlap: **150

**Reasoning:**

---

## Retrieval Approach

<!-- Which embedding model are you using (e.g., all-MiniLM-L6-v2 via sentence-transformers)?
     How many chunks will you retrieve per query (top-k)?
     If you were deploying this for real users and cost wasn't a constraint, what tradeoffs
     would you weigh in choosing a different embedding model — context length, multilingual
     support, accuracy on domain-specific text, latency? -->

**Embedding model: "all-MiniLM-L6-v2"**

**Top-k:**

**Production tradeoff reflection:**

---

## Evaluation Plan

<!-- List your 5 test questions with their expected correct answers.
     Questions should be specific enough that you can judge whether the system's response
     is right or wrong. "What are good dining halls?" is too vague.
     "What do students say about wait times at [dining hall name] during lunch?" is testable. -->

| # | Question | Expected answer |
|---|----------|-----------------|
| 1 | "What is a buffer overflow?"| |
| 2 |"How do I prevent SQL injection attacks?" | |
| 3 |"What are common techniques for privilege escalation?" | |
| 4 | "Can you explain the concept of zero-day vulnerabilities?" | |
| 5 | "What is the difference between symmetric and asymmetric encryption?" | |

---

## Anticipated Challenges

<!-- What could go wrong? Name at least two specific risks with reasoning.
     Consider: noisy or inconsistent documents, missing source attribution, off-topic
     retrieval, chunks that split key information across boundaries. -->

1. Data Source unreachable     

2. Loss of semantic context

3. Model drift mismatch

---

## Architecture

<!-- Draw a diagram of your pipeline showing the five stages:
     Document Ingestion → Chunking → Embedding + Vector Store → Retrieval → Generation
     Label each stage with the tool or library you're using.
     You can use ASCII art, a Mermaid diagram, or embed a sketch as an image.
     You'll use this diagram as context when prompting AI tools to implement each stage. -->

     | Injestion | -> | Chunking | -> | Embedding + Vector store | -> | Retrival | -> | Generation |

     [PDF Books] --> [Ingestion: PyMuPDF/pdfplumber]
             --> [Chunking: LangChain RecursiveCharacterTextSplitter, 450/150]
             --> [Embedding: sentence-transformers all-MiniLM-L6-v2]
             --> [Vector Store: Chroma / FAISS]
             --> [Retrieval: top-k similarity search, k=4-5]
             --> [Generation: Claude API / GPT API with retrieved context]

     

---

## AI Tool Plan

<!-- For each part of the pipeline below, describe:
     - Which AI tool you plan to use (Claude, Copilot, ChatGPT, etc.)
     - What you'll give it as input (which sections of this planning.md, which requirements)
     - What you expect it to produce
     - How you'll verify the output matches your spec

     "I'll use AI to help me code" is not a plan.
     "I'll give Claude my Chunking Strategy section and ask it to implement chunk_text()
     with my specified chunk size and overlap" is a plan. -->



     AI Tool Plan
Milestone 3 — Ingestion and chunking:

Tool: Claude
Input: Documents table + Chunking Strategy section
Expected output: A chunk_documents.py script that extracts text from the 10 PDFs and splits it into 450-char chunks with 150-char overlap, preserving source filename + page number metadata per chunk
Verification: Manually inspect 5-10 random chunks to confirm no mid-sentence definition splits, and confirm metadata correctly maps chunks back to their source book

Milestone 4 — Embedding and retrieval:

Tool: Claude
Input: Retrieval Approach section + chunked output from Milestone 3
Expected output: A script that embeds all chunks with all-MiniLM-L6-v2, stores them in the chosen vector store, and implements a retrieve(query, k=5) function
Verification: Run 2-3 sample queries and manually check retrieved chunks are topically relevant before wiring up generation

Milestone 5 — Generation and interface:

Tool: Claude
Input: Evaluation Plan questions + retrieval function from Milestone 4
Expected output: A generation function that takes retrieved chunks + user query, builds a prompt, and calls the LLM API for an answer; basic CLI or simple UI to ask questions
Verification: Run all 5 evaluation questions, compare answers against expected answers, and check whether responses cite/reflect the correct source book



**Milestone 3 — Ingestion and chunking:  PDF documents of cybersecurity books **

**Milestone 4 — Embedding and retrieval:**

**Milestone 5 — Generation and interface:**
