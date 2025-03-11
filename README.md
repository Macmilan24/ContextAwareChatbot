# Context-Aware Conversational Search System

## Overview

This project is a **context-aware conversational search system** designed to assist users with technical support queries. It maintains context across multiple queries, employs semantic search to deliver relevant answers, and incorporates intent recognition and query recommendations. Developed as part of a trainee program, it showcases fundamental principles of natural language processing (NLP) and interactive user interface design.

The system emulates a chatbot experience, processing user inputs, retaining conversational history, and offering follow-up suggestions through clickable buttons. Implemented in Python within a Jupyter notebook, it leverages Gradio for a seamless, interactive demo.

---

## Features

### 1. Semantic Search

- Utilizes SBERT (`all-MiniLM-L6-v2`) to transform queries and answers into embeddings.
- Matches user queries to the most relevant responses using cosine similarity.

### 2. Context Retention

- Retains up to 3 previous queries in memory.
- Identifies follow-ups (e.g., "how to fix it") by comparing embeddings with a similarity threshold of 0.5, associating them with prior subjects like "screen."

### 3. Intent Recognition

- Detects user intent (repair, replace, install, diagnose, update) through keyword matching from a predefined dictionary.

### 4. Knowledge Graph

- Enriches responses with related concepts (e.g., "screen" → "phone, laptop") derived from a static knowledge graph.

### 5. Recommendations

- Generates follow-up query suggestions based on intent and related terms, presented as interactive buttons that auto-submit upon clicking.

### 6. Chatbot UI

- Built with Gradio, featuring a conversational flow with "You:" and "Bot:" messages.
- Responses are structured with intent, answer, related terms, and recommendations in a clear, readable layout.

---

## How It Works

### 1. Dataset Preparation

- Loads the `yahoo_answers_qa` dataset from Hugging Face, filtered for tech-related categories ("Computers & Internet," "Consumer Electronics," "Yahoo! Products").
- Utilizes a curated subset of 5,000 question-answer pairs to ensure efficient processing while maintaining relevance.

### 2. Embedding Generation

- Employs SBERT to encode answers into embeddings, optimized for performance with GPU support if available.

### 3. Query Processing

- Embeds the user query and compares it to precomputed answer embeddings.
- Assesses prior queries for context, appending a contextual prefix when follow-ups are detected.

### 4. Response Generation

- Determines intent, retrieves the best-matching answer, extracts related concepts from the knowledge graph, and compiles tailored recommendations.

### 5. UI Rendering

- Presents the conversation in an HTML-based chat interface with styled responses and clickable recommendation buttons.

---

## Tools and Why I Used Them

- **Python**: Selected for its extensive NLP libraries and suitability for rapid prototyping in Jupyter notebooks.
- **SentenceTransformers (SBERT)**: Employed for its efficient semantic embeddings (`all-MiniLM-L6-v2` offers a balance of speed and accuracy).
- **Datasets**: Facilitates seamless loading and filtering of the Yahoo Answers dataset from Hugging Face.
- **Gradio**: Chosen for its straightforward interface creation, enabling an interactive chatbot demo.
- **NLTK**: Provides tokenization capabilities for potential future enhancements.
- **NumPy & Torch**: Essential for tensor operations and embedding computations, ensuring compatibility with SBERT.
- **NetworkX**: Utilized to construct the knowledge graph, supporting structured relationships among tech concepts.
- **Scikit-Learn**: Included for cosine similarity calculations.
- **Pandas**: Added for potential data manipulation during development.

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Macmilan24/ContextAwareChatbot.git
cd ContextAwareChatbot
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the Notebook

- Open `yahoo_tech_chat.ipynb` in Jupyter or Colab.
- Execute all cells in sequence to load the dataset, generate embeddings, and launch the Gradio interface.

### 4. Interact

- Enter a query (e.g., "my laptop screen is broken") in the textbox.
- Click "Send" or press Enter to view the response.
- Use recommendation buttons to explore related queries.

---

## Example Interaction

```text
You: my laptop screen is broken
Bot:
Intent: repair
Response: LCD monitor? Dont think you can. I believe you would have to replace the entire LCD...
Related: phone, laptop, screen
Recommendations:
[How to fix a screen?] [How to replace a screen?]

You: how to fix it
Bot:
Intent: repair
Response: It seems you're referring to 'screen' from before: [screen repair advice]
Related: phone, laptop
Recommendations:
[How to fix a screen?] [How to replace a screen?]
```

---

## Limitations

- **Dataset Scope**: Limited to 5,000 entries, which may exclude some relevant tech support scenarios.
- **Response Precision**: Yahoo Answers data can include informal or vague answers, impacting reliability.
- **Context Sensitivity**: Similarity-based context detection may overlook complex follow-ups.

---

## Future Improvements

- Expand the dataset with curated tech support sources (e.g., Stack Overflow or official manuals).
- Implement advanced context resolution techniques, such as entity recognition.
- Enhance intent detection with machine learning models for greater accuracy.

---

## Credits

Developed by Samuel Dagne as part of Group 2 Trainee Program, March 2025.

```

```
