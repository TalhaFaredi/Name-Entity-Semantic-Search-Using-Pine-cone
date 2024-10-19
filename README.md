
**This project implements a semantic search system using Named Entity Recognition (NER) for filtering.**

**Functionality:**

* Processes a dataset of Medium articles
* Extracts named entities using a pre-trained NER model
* Generates sentence embeddings for each article
* Stores embeddings and metadata in a Pinecone index
* Allows querying the index based on natural language text 
* Filters results based on extracted named entities

**Setup:**

1. Install required libraries (refer to code for details)
2. Configure Pinecone API Key and Environment variables
3. Download pre-trained NER and Sentence Transformer models

**Data Preparation:**

* Loads a sample of Medium articles from a dataset
* Prepares "text_extended" field by concatenating title and first 1000 characters of text
* Cleans and preprocesses data (refer to code for specifics)

**Building the Index:**

* Creates a Pinecone index with appropriate dimension and metric
* Loops through data in batches
    * Generates sentence embeddings for each batch
    * Extracts named entities for each document
    * Creates a list with document IDs, embeddings, and metadata
    * Upserts data into the Pinecone index

**Querying the System:**

* Takes a natural language query as input
* Generates a query vector using the Sentence Transformer
* Extracts named entities from the query
* Queries the Pinecone index with the query vector
* Filters results based on matching named entities

**Example Usage:**

```
Query: "How to make a Wordpress website?"

Output:

0.294890732  ['Wordpress', 'Both Sides of the Table']
0.207520485  ['Wordpress', 'Opencart', ...]  # (truncated list)
0.187706783  ['CMS', 'Wordpress', ...]  # (truncated list)
...
```

