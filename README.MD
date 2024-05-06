# **Information Retrieval System Report**

## Natural Language Processing: Boolean Retrieval
**Author: Artur Papyan**

### Objective
The goal of this project was to design and implement an information retrieval system capable of parsing complex queries with logical operators and returning relevant documents from an inverted index. The system was specifically designed to support queries in both English (ENG) and Czech (CZE), and was evaluated for its performance in terms of precision and recall.

### Methodology
#### XML Parser
- **Implementation**: The system is implemented in the Python programming language using the `lxml` library's `etree` class to parse XML documents. This facilitates data retrieval and the creation of an inverted index dictionary.
- **Tokenization**: Queries are first tokenized, breaking down the query string into keywords, operators, and parentheses for precedence and nesting.
- **Syntax Tree Construction**: Tokens are used to construct a syntax tree, where each node represents an operator (AND, OR, NOT) or a term (keyword). This structure helps interpret the query's logical structure.
- **Evaluation**: 
  - For binary operators (AND, OR), it involves finding the intersection or union, respectively, of the document sets associated with the node's children.
  - For the unary operator (NOT), the evaluation involves subtracting the document set of its child from the universal set of documents, ensuring accurate retrieval.

#### Handling the NOT Operator
- A unique challenge in the implementation was correctly handling the NOT operator, which negates a single operand. The logic was modified to directly apply NOT to the following token or nested expression.

#### How to Run?
- Open the `boolean_retrieval.ipynb` file in a Jupyter notebook environment.
- Update the file path variables (`documents_en_filepath`, `documents_cz_filepath`, etc.) to your desired ones as described in the notebook.
- Execute the notebook to print the results and output the files to the specified directories.

### Results
The system achieved the following average precision and recall scores across the datasets:

#### English (ENG)
- **Average Precision**: 0.8598
- **Average Recall**: 0.8323

#### Czech (CZE)
- **Average Precision**: 0.798
- **Average Recall**: 0.754

### Conclusions
The system demonstrates foundational capabilities in processing and interpreting complex queries with logical operators, providing a robust basis for retrieving relevant documents from an inverted index. The performance metrics provide insights into the system's effectiveness, highlighting areas for further investigation, particularly the lack of token normalization (as it was not requested).
