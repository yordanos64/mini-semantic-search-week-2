# Mini Semantic Search

This is my Week 2 lab project for the AI/ML AWS AASTU Cohort. The goal was to build a small search system that can find FAQs related to a user's question.

I used Pandas to load and clean the FAQ data, then ChromaDB to create embeddings and search for similar questions. The notebook shows the process from loading the data to retrieving the top three results.

## Dataset

I used a CSV file named `faqs.csv` containing 10 sample FAQs about an online learning platform. Each record has an ID, a question, and an answer.

Before creating the searchable text, I checked the dataset for missing values and duplicate question-and-answer pairs. I then cleaned the text and combined each question with its answer into one chunk.

## How the Search Works

ChromaDB generates an embedding for each FAQ and stores it in a collection. When a user enters a question, the system searches for the most similar stored FAQ chunks and returns the top three matches.

For example, I searched for:

`I forgot my password. How can I get back into my account?`

The first result was **How can I reset my password?**, with the answer: “Select Forgot Password on the login page.”

The search also returned an FAQ about login problems and another about contacting support. This shows how the system can find related information even when the wording of the search query is different from the stored question.

## Running the Project

The notebook is named `Mini_Semantic_Search.ipynb`, and the FAQ data is stored in `data/faqs.csv`. To run the project locally, Python must be installed.

Create a virtual environment and install the required packages using:

powershell
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt


Open the notebook in VS Code, select the `.venv` Python environment as the kernel, and run the cells in order.

ChromaDB's default embedding model may need to download its files on the first run, so an internet connection is required if the model is not already available locally.

## Files

`Mini_Semantic_Search.ipynb` contains the code and outputs for the lab. `data/faqs.csv` contains the sample FAQ data. `requirements.txt` lists the Python packages needed to run the project, and `.gitignore` excludes local files such as the virtual environment and generated ChromaDB database.

## Limitations

This project uses a small sample dataset, so the search results depend on the FAQs available in the collection. It retrieves relevant text but does not generate answers with an LLM.

