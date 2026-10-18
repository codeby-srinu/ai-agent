# hackathon
# 🎓 Previous-Year Question Paper Bot

An AI-powered question retrieval chatbot that helps students find relevant exam questions using semantic similarity search.

## 📌 Project Overview

The Previous-Year Question Paper Bot is a Python-based web application designed to simplify exam preparation. Students can select a subject, such as Database Management Systems (DBMS) or Data Structures, and search for questions through a chatbot interface.

The system uses Natural Language Processing (NLP), Sentence Transformers, and FAISS to identify questions that are semantically similar to a user's query.

Unlike generative AI chatbots, this application retrieves and displays existing questions directly from its dataset without using a separate Large Language Model (LLM) to generate answers.

## 🎯 Problem Statement

Students often spend considerable time manually searching through question papers to find questions related to specific topics. Traditional keyword-based searches can miss relevant questions when their wording differs.

This project addresses the problem by retrieving questions based on semantic meaning rather than exact keyword matches.

## ✨ Features

- **Semantic question search:** Finds questions related to the meaning of a query.
- **Subject selection:** Supports subjects such as DBMS and Data Structures.
- **Similarity ranking:** Displays the most relevant questions based on similarity scores.
- **Question metadata:** Shows the associated subject and year when available.
- **Interactive chatbot:** Provides a simple web interface using Gradio.
- **Extensible dataset:** Supports adding questions and subjects to the dataset.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Google Colab | Development and execution environment |
| Pandas | Organizes and filters the question dataset |
| NumPy | Numerical operations |
| Sentence Transformers | Converts questions into semantic embeddings |
| all-MiniLM-L6-v2 | Pretrained embedding model |
| FAISS | Stores vectors and retrieves similar questions |
| Gradio | Creates the chatbot web interface |
| Matplotlib | Optional topic trend visualization |
| Git and GitHub | Version control and project hosting |

## 🧠 System Architecture

```text
                Student Query
                     |
                     v
              Gradio Frontend
                     |
                     v
              Query Embedding
           (Sentence Transformers)
                     |
                     v
                FAISS Search
                     |
                     v
            Similarity Ranking
                     |
                     v
            Relevant Questions
                     |
                     v
              Chatbot Results
```

## ⚙️ How It Works

### 1. Dataset Preparation

Questions are stored in a structured dataset containing fields such as subject, year, and question text.

### 2. Embedding Generation

The `all-MiniLM-L6-v2` Sentence Transformer converts each question into a 384-dimensional numerical vector representing its semantic information.

### 3. Vector Indexing

FAISS stores the question embeddings in a vector index. The project uses `IndexFlatIP` with normalized embeddings to perform exact similarity searches equivalent to cosine similarity.

### 4. Query Processing

When a student enters a question, the same embedding model converts the query into a vector.

### 5. Semantic Retrieval

FAISS compares the query vector with stored question vectors and retrieves the most similar questions.

### 6. Result Display

The Gradio interface displays the retrieved questions, along with available subject and year information and similarity scores when enabled.

## 🔍 Understanding Similarity Scores

Similarity scores indicate how closely a retrieved question matches the user's query in embedding space.

For example, a query about database normalization may retrieve questions about functional dependencies, normal forms, and normalization objectives.

A higher score indicates greater semantic closeness, but it does not necessarily mean that two questions are identical.

Similarity scores are not repetition counts or predictions of future examination questions.

## 🚀 Getting Started

### Prerequisites

- A Google account for Google Colab
- An internet connection for downloading dependencies and the embedding model
- A Python environment
- A question dataset

### Installation

Run the following command in Google Colab:

```python
%pip install -q numpy pandas faiss-cpu sentence-transformers gradio matplotlib
```

### Execution Steps

1. Load the question dataset into a Pandas DataFrame.
2. Load the Sentence Transformer model.
3. Generate embeddings for all questions.
4. Create the FAISS vector index.
5. Define the semantic retrieval function.
6. Launch the Gradio chatbot.
7. Select a subject and enter a question to retrieve relevant results.

## 💬 Example Usage

**User query:**

```text
Find questions related to normalization in DBMS.
```

**Expected workflow:**

1. The query is converted into an embedding.
2. FAISS searches the question index.
3. The system ranks the matching questions by similarity.
4. The chatbot displays the retrieved questions.

The results depend on the contents and quality of the dataset.

## 📁 Suggested Project Structure

```text
previous-year-question-bot/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── questions.csv
│
├── notebooks/
│   └── question_paper_bot.ipynb
│
└── src/
    ├── data_loader.py
    ├── embeddings.py
    ├── retrieval.py
    └── app.py
```

This is a suggested structure; adjust it to match your actual repository.

## 🔮 Future Enhancements

- Add verified previous-year examination papers.
- Support PDF uploads and automatic question extraction.
- Group semantically similar questions to identify repeated patterns.
- Add more subjects and institutions.
- Improve subject-specific filtering.
- Add a question similarity threshold.
- Allow users to upload their own datasets.

## ⚠️ Limitations

- Retrieval quality depends on the dataset's coverage and accuracy.
- Similarity scores may not perfectly represent a question's relevance.
- The system does not generate new answers or explanations using an LLM.
- Historical trends cannot be verified unless the underlying data comes from verified past papers.

If the dataset contains representative practice questions, describe the results as retrieval from a practice dataset rather than verified historical exam patterns.

## 👨‍💻 Project Purpose

This project demonstrates how semantic embeddings and vector search can be used to build an AI-powered educational search application without requiring a separate generative LLM.

## 📄 License

Choose a suitable license for your own code before publishing the repository. Check the licenses of your datasets and dependencies separately.
