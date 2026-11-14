# 📚 BookBuddy – AI-Powered Book Recommendation Chatbot

BookBuddy is an AI-powered book recommendation chatbot that helps readers discover books based on their interests, preferred genres, moods, themes, and reading preferences.

It uses a **Retrieval-Augmented Generation (RAG)** pipeline to retrieve relevant books from a curated English-language book dataset and generates personalized recommendations using a Large Language Model (LLM).

## ✨ Features

- **Personalized Recommendations:** Discover books based on genres, moods, themes, and reading interests.
- **Semantic Search:** Find relevant books using natural-language queries rather than exact keyword matches.
- **AI-Powered Explanations:** Get a reason explaining why each recommended book matches your preferences.
- **Book Details:** View book titles, authors, genres, descriptions, and available ratings.
- **Book Covers:** Display book cover images using the Open Library API when available.
- **Interactive Chat Interface:** Explore recommendations through a conversational Streamlit interface.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data preprocessing and cleaning |
| Sentence Transformers | Text embedding generation |
| all-MiniLM-L6-v2 | Semantic embedding model |
| FAISS | Vector similarity search |
| Groq API | Large Language Model inference |
| Streamlit | Interactive chatbot frontend |
| Open Library API | Book cover image retrieval |

## 🧠 How It Works – RAG Architecture

BookBuddy uses a custom Retrieval-Augmented Generation pipeline without relying on frameworks such as LangChain.

The workflow consists of the following steps:

1. **Data Preprocessing:** The book dataset is cleaned, filtered to retain English-language books, and transformed into searchable text.
2. **Text Embeddings:** The Sentence Transformer model (`all-MiniLM-L6-v2`) converts book descriptions and metadata into numerical embeddings.
3. **Vector Database:** FAISS stores the embeddings and enables efficient similarity search.
4. **Semantic Retrieval:** When a user submits a query, it is converted into an embedding and compared with stored book embeddings.
5. **AI Recommendation Generation:** Relevant books are passed to the Groq-hosted LLM, which generates recommendations and explanations.
6. **Frontend Display:** Streamlit displays the recommendations, book information, and available cover images.

### Architecture Overview

```text
              User Query
                   |
                   v
          Streamlit Chat Interface
                   |
                   v
            Query Embedding
                   |
                   v
             FAISS Search
                   |
                   v
        Relevant Book Retrieval
                   |
                   v
          Groq LLM (gpt-oss-20b)
                   |
                   v
       Personalized Recommendations
                   |
                   v
          Streamlit Book Cards
                   |
                   v
             User Response
```

## 📂 Project Structure

```text
BookBuddy-AI/
│
├── app.py
├── requirements.txt
├── .gitignore
│
├── data/
│   └── english_books.csv
│
├── src/
│   ├── preprocess.py
│   ├── build_vectorstore.py
│   ├── retrieve_books.py
│   └── groq_chat.py
│
└── vectorstore/
    ├── books.index
    └── book_metadata.pkl
```

## 🚀 Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/DokkaChinnari/BookBuddy-AI.git
cd BookBuddy-AI
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```powershell
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Groq API Key

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

Get your API key from [Groq Console](https://console.groq.com/).

**Important:** Never upload your `.env` file or expose your API key publicly.

### 5. Run the Application

```bash
streamlit run app.py
```

The application will open in your browser, usually at:

```text
http://localhost:8501
```

## 📊 Dataset

BookBuddy uses the **Books Prices Prediction** dataset from Kaggle.

Dataset source: [Kaggle – Books Prices Prediction](https://www.kaggle.com/competitions/book-prices-prediction/data)

The preprocessing pipeline combines the available training and test datasets, filters English-language books, cleans the records, and creates the final `english_books.csv` file.

The generated FAISS index and metadata are stored in the `vectorstore/` directory.

## 🔍 Technologies and Concepts Demonstrated

This project demonstrates practical implementation of:

- Retrieval-Augmented Generation (RAG)
- Natural Language Processing (NLP)
- Text Embeddings
- Semantic Similarity Search
- Vector Databases
- Large Language Model Integration
- Data Cleaning and Preprocessing
- API Integration
- Interactive Web Application Development

## 🔮 Future Improvements

- Add user profiles and personalized reading history.
- Improve recommendation relevance using user feedback.
- Add book ratings and reviews from external sources.
- Expand the dataset with additional book information.
- Add filters for authors, publication years, and ratings.
- Deploy the application publicly for wider access.

## 👩‍💻 Author

Dokka Chinnari
B.Tech - Artificial Intelligence & Machine Learning

Passionate about Data Analytics, Power BI, SQL, Python, and Machine Learning.

GitHub: https://github.com/DokkaChinnari

LinkedIn: https://www.linkedin.com/in/dokka-chinnari-aiml/

⭐ If you find BookBuddy interesting, consider giving the repository a star!
