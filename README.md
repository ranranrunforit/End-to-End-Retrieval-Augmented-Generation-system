# End-to-End Retrieval Augmented Generation (RAG) System for Answering Questions

## Overview

This repository contains the implementation of a Retrieval Augmented Generation (RAG) ([Lewis et al., 2021](https://arxiv.org/abs/2005.11401)) system designed to answer questions about Pittsburgh and CMU.

## Task Specification

The project focused on factual question-answering (QA) ([Touvron et al., 2023](https://arxiv.org/abs/2307.09288)) specifically regarding Pittsburgh and CMU. The system first retrieved relevant documents and then generated answers based on those documents. The system adopted large language models (LLMs) such as Llama 3.2 to enhance the knowledge base with relevant documents, thereby improving the accuracy of answers related to history, culture, trivia, and upcoming events.

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

Utilized [langchain&#39;s RAG stack](https://python.langchain.com/docs/use_cases/question_answering/local_retrieval_qa) to construct the system.

### RAG Strategies

Experimented serveral RAG strategies to improve performance:

- **Custom Text Splitters:** Experimented with different types of splitters, including recursive, character, token, and semantic splitters.
- **Embedding Models:** Compared multiple embedding models, such as `sentence-transformers/all-MiniLM-L6-v2` and `sentence-transformers/all-MiniLM-L12-v2`.
- **Document Retrieval Methods:** Evaluated FAISS and CHROMA retrievers with different algorithms, such as similarity search and MMR.
- **Reranking:** Implemented reranking using models like `ms-marco-MiniLM-L-12-v2` and `ms-marco-MultiBERT-L-12`.
- **Hypothetical Document Embeddings (HyDE):** Used hypothetical document embeddings ([Gao et al., 2022](https://arxiv.org/abs/2212.10496)) to improve retrieval quality.

## Result Generation

Executed the system on an unseen test set to evaluate its performance. 

### Evaluation Metrics

Results were evaluated based on standard metrics including answer recall, exact match, and F1 score, following the methodology outlined in section 6.1 of the [original SQuAD paper](https://arxiv.org/abs/1606.05250) .

## Usage Instructions

### Hardware Requirements
The project required a machine with:

- GPU memory >= 20GB
- CUDA support
- At least 50GB available disk space

### API Keys

Set up the API keys for [LangChain](https://www.langchain.com) and [Hugging Face](https://huggingface.co/models) to access Llama-3.2.

## References

+ Lewis et al., 2021. [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://arxiv.org/abs/2005.11401).
+ Touvron et al., 2023. [Llama 2: Open Foundation and Fine-Tuned Chat Models](https://arxiv.org/abs/2307.09288).
+ Vu et al., 2023. [FreshLLMs: Refreshing Large Language Models with Search Engine Augmentation](https://arxiv.org/abs/2310.03214).

