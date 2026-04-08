# Offline-Information-Retrieval-IR-Search-System-Python-Flask-

##  Overview  

Social media and review platforms generate large volumes of textual data. Analyzing such data in real-time often depends on paid APIs or complex infrastructure.  

This project builds an **Offline Information Retrieval (IR) System** that works on static datasets (CSV files).  

The system demonstrates core IR concepts by allowing users to:

-  Search documents using keyword queries  
-  Retrieve ranked results using similarity scoring  
-  View short snippets of relevant documents  
-  Analyze grouped keyword frequency trends  
-  Evaluate retrieval performance using Precision@K  

The entire system works **offline and reproducibly** using a consistent IR processing pipeline.

---

##  Objectives  

- Build an indexing and search system for text-based datasets  
- Implement TF-IDF document representation  
- Apply the Vector Space Model with cosine similarity  
- Provide ranked search results  
- Perform descriptive keyword trend analysis  
- Include basic IR evaluation (Precision@K)  
- Deploy the system using a web interface  

---

## System Architecture  
Static Dataset (CSV)
↓
Preprocessing (merge text fields, stopword removal)
↓
TF-IDF Indexing
↓
Vector Space Model (Cosine Similarity)
↓
Top-K Ranking
↓
Trend Grouping + Precision@K
↓
Flask Web Interface


---

##  Dataset  

The system is configurable and can work with multiple datasets.

### Current Active Dataset (Electronics Reviews)

- **Type:** Product Reviews  
- **Format:** CSV  
- **Source:** Local dataset (`ElectronicsData.csv`)  
- **Text Fields Used:** `Title`, `Feature`, `Sub Category`  
- **Grouping Column:** `Price`  

Each row in the dataset is treated as a **document**.

The system can also be configured to work with:
- Twitter datasets  
- News datasets  
- Review datasets  
- Any structured text dataset in CSV format  

To change datasets, update the following in `main.py`:

URL = ...
COLS = [...]
DATE = ...


##  Indexing and Representation
- Preprocessing
- Selected text columns are merged into a single field (search_content)
- Missing values handled using fillna('')
- Lowercasing applied automatically
- English stopwords removed
- Document Representation
- Documents are represented using:
- TF-IDF (Term Frequency – Inverse Document Frequency)
- Implemented using TfidfVectorizer from scikit-learn
- Each document becomes a TF-IDF vector in high-dimensional space.

This satisfies:
- Tokenization
- Stop-word removal
- Term frequency weighting
- TF-IDF representation

##  Retrieval Model

The system uses the Vector Space Model (VSM).

Retrieval Process:
- User enters a query
- Query is converted into a TF-IDF vector
- Cosine similarity is calculated between the query and all documents
- Documents are ranked in descending order of similarity
- Top-K documents are displayed

 ## Trend Analysis

The system performs descriptive trend analysis by:
- Filtering documents that contain the query term
- Grouping matched documents by a selected column
- Counting occurrences per group

## For the current dataset:

- Grouped by Price
- Shows how frequently a keyword appears across price values
- If using a timestamp column (e.g., created_at or tweet_created), the system can represent keyword frequency over time.

## Search Interface
The system includes a web-based search interface built with:
- Flask (Backend)
- Bootstrap 5 (Frontend)
Features:
- Search input field
- Ranked result cards
- Short document snippets (first 200 characters)
- Highlighted query terms
- Precision@K badge
- Trend frequency sidebar
- “Load More” functionality

## This satisfies the requirement for: 
- Web interface
- Ranked retrieval
- Snippet display
- Highlighted terms

 ## Tech Stack
- Category	Tools / Libraries
- Language	Python
- Backend	Flask
- Data Handling	pandas
- IR Model	scikit-learn (TF-IDF)
- Similarity	Cosine Similarity
- Frontend	Bootstrap 5
- Hosting	PythonAnywhere

## Hosting

The system is designed for deployment using:
- Flask WSGI configuration
- PythonAnywhere

## Beneficiaries
Beneficiary Group	How They Benefit
- IR / NLP Students	Understand TF-IDF, cosine similarity, and ranking
- Educators	Demonstrate core IR concepts offline
- Researchers	Test retrieval performance on static datasets
- Analysts	Perform keyword-based frequency analysis

## Real-World Applications
- Keyword-based document search
- Trend frequency analysis
- Academic IR demonstrations
- Offline text dataset exploration

## Limitations
- No manual ground-truth relevance labels
- No stemming or lemmatization
- No semantic query expansion
- Trend analysis depends on selected grouping column
- No advanced clustering or topic modeling

## Conclusion

This project demonstrates core Information Retrieval principles:
- TF-IDF indexing
- Vector Space Model
- Cosine similarity ranking
- Precision@K evaluation
- Keyword frequency grouping
- Web-based search interface

## The system provides a modular and reproducible offline IR framework suitable for academic demonstration and experimentation.
