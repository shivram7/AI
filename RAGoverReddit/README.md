README
# RAG on Reddit Data

## Overview
This project processes Reddit submissions and comments from specified subreddits using Amazon S3 as the data source. The pipeline consists of three main stages:
1. **Data Preparation (data_prep.ipynb)** - Fetches Reddit submissions and comments from S3, filters for specific subreddits, and merges the data.
2. **Loading Data into a Vector Database (load_data_in_vdb.ipynb)** - Prepares and stores the processed Reddit data into a vector database.
3. **Retrieval-Augmented Generation (rag.ipynb)** - Implements RAG techniques using the stored data to enable efficient querying and retrieval of relevant Reddit discussions.

## Files
### 1. `data_prep.ipynb`
- Connects to the Amazon S3 bucket `bigdatateaching`.
- Retrieves Reddit submissions and comments from January 2024.
- Filters for the subreddits: `AskNYC` and `washingtondc`.
- Merges submissions and comments based on parent-child relationships.
- Converts the processed data into JSON format and saves it as `reddit_AskNYC_washingtondc.json`.

### 2. `load_data_in_vdb.ipynb`
- Loads the processed JSON file.
- Uses `RecursiveJsonSplitter` from `langchain` to create documents from the JSON data.
- Generates embeddings using `HuggingFaceBgeEmbeddings`.
- Extracts metadata from documents.
- Stores embeddings in a FAISS index for efficient similarity search.
- Saves the FAISS index and metadata to disk.

### 3. `rag.ipynb`
- Implements a Retrieval-Augmented Generation (RAG) system.
- Utilizes the vector database to answer queries based on Reddit discussions.
- Enhances retrieval efficiency for topic-based questions.

## Dependencies
- Python
- `pandas`
- `pyarrow`
- `boto3`
- `json`
- `re`
- `langchain`
- `faiss`
- `numpy`
- `HuggingFaceBgeEmbeddings`

## Running the Pipeline
1. Run `data_prep.ipynb` to fetch and preprocess the data.
2. Run `load_data_in_vdb.ipynb` to load the processed data into the vector database.
3. Run `rag.ipynb` to execute queries using retrieval-augmented generation.

## Output
- **Processed Reddit Data:** `reddit_AskNYC_washingtondc.json`
- **Vector Database:** Stores structured Reddit discussions.
- **FAISS Index:** Stores document embeddings for fast similarity search.
- **Query System:** Enables efficient retrieval of Reddit insights based on user queries.

## Future Improvements
- Expand subreddit filtering criteria.
- Optimize vector database storage and retrieval performance.
- Enhance the RAG model for better contextual understanding.



