# End-to-End Retrieval Augmented Generation (RAG) System

## Overview

This repository contains the implementation of a Retrieval Augmented Generation (RAG) system designed to answer questions about Pittsburgh and CMU. The system utilized large language models (LLMs) such as Llama3.2 to enhance the knowledge base with relevant documents, thereby improving the accuracy of answers related to history, culture, trivia, and upcoming events.

## Task Specification

The project focused on factual question-answering (QA) specifically regarding Pittsburgh and CMU. The system first retrieved relevant documents and then generated answers based on those documents.

## Key Checkpoints

- **Raw Data Preparation:** Compiled a knowledge resource of relevant documents from various sources.
- **Data Annotation:** Annotated data for both testing/analysis and training purposes.
- **RAG System Development:** Developed a retrieval augmented generation system using open-source models and libraries.
- **Result Generation:** Generated answers using the constructed system and validated against reference answers.

## Data Format

- **Input:** A text file `questions.txt` containing one question per line.
- **Output:** A text file `system_output.txt` containing system-generated answers corresponding to the questions.
- **Reference:** A text file `reference_answers.txt` with correct answers for evaluation.

## Data Preparation

### Knowledge Resource Compilation

The knowledge resource included a mix of HTML pages, PDFs, and plain text documents from recommended sources such as:

- Wikipedia pages on Pittsburgh and its history.
- The City of Pittsburgh official webpage.
- Event calendars from Visit Pittsburgh and CMU.
- Information regarding music, culture, and sports in Pittsburgh.

### Data Collection

Created a clean dataset for model development:

- Processed HTML pages using `beautifulsoup4`
- Parsed PDF documents with `pypdf2`, `PyMuPDF`, `pdf2image`, and `pytesseract`

## Data Annotation

Annotated question-answer pairs:

- Curated a diverse set of questions relevant to Pittsburgh and CMU, ensuring high quality and domain relevance.
- Annotated examples manually and explored existing datasets for transfer learning.

### Quality Estimation

Measured inter-annotator agreement (IAA) to assess the quality of annotations, ensuring reliability in the test dataset.

## RAG System Development

Developed the RAG system with the following components:

1. **Document & Query Embedder**
2. **Document Retriever**
3. **Document Reader (Question-Answering System)**

Utilized LangChain’s open-source libraries to construct the system.

## Result Generation

Executed the system on an unseen test set to evaluate its performance. 

### Evaluation Metrics

Results were evaluated based on standard metrics including answer recall, exact match, and F1 score, following the methodology outlined in the SQuAD paper.

## Usage Instructions

The project required a machine with:

- GPU memory > 20GB
- CUDA support
- At least 50GB available disk space

Set up the API keys for LangChain and Hugging Face to access Llama-3.1 and Llama-3.2.
