# Summary of the current content

This notebook performs the following tasks:

1. **Setup and Imports**
   - Installs the required OpenAI library.
   - Imports necessary libraries for data processing and AI functions.

2. **Data Ingestion**
   - Loads call log data (`contoso_financial_support_logs_v3.csv`) from the default Lakehouse into a Pandas DataFrame.

3. **Data Cleaning**
   - Removes the `Sentiment` column if it exists.
   - Drops duplicate rows from the dataset.

4. **Data Enrichment with AI Functions**
   - Translates the `Description`, `Notes`, and `CallTranscript` columns to English.
   - Analyzes sentiment in the English call transcript.
   - Classifies each issue into categories: `documents`, `scheduling`, `trading`, `reporting`, `bug`.
   - Summarizes each call transcript.

5. **Conversion and SQL Integration**
   - Converts the enriched Pandas DataFrame into a Spark DataFrame.
   - Registers the DataFrame as a temporary SQL view for further queries.

6. **Lakehouse Table Creation**
   - Extracts and saves unique values for `IssueCategory`, `DeskName`, and `AgentName` as separate Delta tables in the default Lakehouse.
   - Saves the final, processed call logs as a Delta table (`callLogs`) in the Lakehouse.
  
7. **Azure AI Search Document Ingestion Pipeline**
   - This notebook processes PDF documents and creates a searchable vector database in Azure AI Search, designed for RAG (Retrieval-Augmented Generation) scenarios where you need to search through document content using both keywords and semantic similarity.
   - Ingests PDF documents from Azure storage (OneLake/Fabric lakehouse), extracts their content using Azure Document Intelligence, chunks the text, generates embeddings, and indexes everything into Azure AI Search for hybrid search (keyword + vector search).

> **In summary:**  
> The notebook ingests, cleans, enriches, classifies, and saves call log data using both Pandas and Spark, leveraging AI capabilities to make the data ready for downstream analytics in Microsoft Fabric.
