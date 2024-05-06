***Information Retrieval System Report***
Natural Language Processing
Boolean Retrieval
Artur Papyan

Objective
The goal of the work was to design and implement an information retrieval system, which needed to parse the data and queries from XML files and be capable of parsing those complex queries with logical operators and returning relevant documents from an inverted index. The system was designed to support queries specifically in English (ENG) and Czech (CZE), and to evaluate its performance in terms of precision and recall.

Methodology
•	XML Parser
I have implemented the system in Python programming language.
The system utilizes “lxml” libraries “etree” class to parse the XML documents and retrieve the data (and by using it create the inverted index dictionary). Then it iterates over those texts, tokenizes them and creates the inverted index dictionary. As I have used “set” data structure as values for storing document IDs in inverted index dictionary, there is no need to sort the document IDs, as “set” data structure have union, intersect built-in functions.
•	Parsing Process:
•	Tokenization: The first step in processing a query is tokenization, where the query string is broken down into identifiable pieces, including keywords, operators, and parentheses for indicating precedence and nesting.
•	Syntax Tree Construction: The tokens are then used to construct a syntax tree, where each node represents an operator (AND, OR, NOT) or a term (keyword). This tree structure allows me to interpret the query's logical structure and evaluate it against the inverted index.
•	Evaluation: The syntax tree is evaluated by recursively processing each node. For binary operators (AND, OR), the evaluation involves finding the intersection or union, respectively, of the document sets associated with the node's children. For the unary operator (NOT), it involves subtracting the document set of its child from the universal set of documents.
Handling the NOT Operator: A unique challenge in my implementation was correctly handling the NOT operator, which negates a single operand. Unlike AND and OR, NOT does not combine two sets but rather filters out documents from a universal set that do not match the operand. To address this, I modified the evaluation logic to directly apply NOT to the following token or nested expression, ensuring accurate retrieval of documents.
•	How to run?
In order to run the program, firstly open the “boolean_retrieval.ipynb” (e.g. Jupyter notebook) file and fill the “documents_en_filepath”, “documents_cz_filepath”, “topics_train_en_filepath”, “topics_train_cz_filepath”, “qrels_train_en_filepath”, “qrels_train_cz_filepath”, “queries_answers_en_filename”, “queries_answers_cz_filename” variable to your desired ones (the description of the files are written in the file), then run the “boolean_retrieval.ipynb”. It will print the results and output the resulting files to the directories that you mentioned in the “queries_answers_en_filename”, “queries_answers_cz_filename”.


Results
My system achieved the following average precision and recall scores across the datasets:
•	English (ENG)
	o	Average Precision: 0.8598
	o	Average Recall: 0.8323
•	Czech (CZE)
	o	Average Precision: 0.798
	o	Average Recall: 0.754

Conclusions
The system demonstrates a foundational capability to process and interpret complex queries with logical operators, providing a basis for retrieving relevant documents from an inverted index. While the performance metrics provide insight into the system's effectiveness, the noted discrepancy between the system's output and the ground truth highlights an area for further investigation and most importantly lack of normalization of tokens (as it was not requested).


