# 🚀 RAG on NFcorpus

<div align="center">

[![Python](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/)
[![Google AI](https://img.shields.io/badge/Google%20AI-Gemini-4285F4)](https://ai.google.dev/)
[![RAGAS](https://img.shields.io/badge/eval-RAGAS-green)](https://github.com/explodinggradients/ragas)
[![License](https://img.shields.io/badge/license-MIT-yellow)](LICENSE)
[![Docs](https://img.shields.io/badge/docs-latest-blue)](notebooks/)

**High-Performance Retrieval-Augmented Generation on BEIR/NFcorpus Dataset**

[Features](#-features) • [Installation](#-installation) • [Quick Start](#-quick-start) • [Documentation](#-documentation) • [Results](#-results)

</div>

---

## 📋 Overview

This project implements state-of-the-art Retrieval-Augmented Generation (RAG) techniques optimized for the BEIR/NFcorpus dataset. We provide both a robust baseline implementation and an enhanced variant with significant performance improvements, all evaluated using the comprehensive RAGAS framework.

### 🎯 Key Objectives
- **Establish a solid baseline** RAG pipeline for benchmark comparison
- **Develop enhanced techniques** to improve retrieval and generation quality
- **Rigorous evaluation** using industry-standard RAGAS metrics
- **Reproducible results** with clear documentation and code

## ✨ Features

- 🔍 **Advanced Retrieval Pipeline** - Optimized embedding and retrieval strategies
- 🤖 **Gemini Integration** - Leveraging Google's latest LLM capabilities
- 📊 **Comprehensive Evaluation** - Multi-metric assessment using RAGAS
- 📁 **Pre-processed Datasets** - Ready-to-use formatted data files
- 🔧 **Modular Architecture** - Easy to extend and customize
- 📝 **Detailed Notebooks** - Step-by-step implementation guides

## 🗂️ Project Structure

```
rag-nfcorpus/
│
├── 📓 notebooks/
│   ├── baseline_RAG.ipynb      # Baseline implementation & evaluation
│   ├── improved_RAG.ipynb      # Enhanced RAG experiments
│   ├── get_corpus.ipynb        # Corpus preparation utilities
│   ├── get_query.ipynb         # Query processing pipeline
│   └── get_qrels.ipynb         # Relevance labels extraction
│
├── 📊 assets/
│   ├── train.csv               # Training dataset
│   ├── validation.csv          # Validation dataset
│   ├── test.csv                # Test dataset
│   ├── corpus.csv              # Document corpus
│   └── queries.csv             # Query collection
│
├── 📄 LICENSE
├── 📖 README.md
└── 🔐 .env.example
```

## 🚀 Installation

### Prerequisites

- Python 3.9 or higher
- CUDA-compatible GPU (optional, for faster embeddings)
- Google AI API access

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/rag-nfcorpus.git
   cd rag-nfcorpus
   ```

2. **Create virtual environment**
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -U google-generativeai ragas pandas numpy scikit-learn jupyter python-dotenv
   ```

4. **Configure environment variables**
   ```bash
   cp .env.example .env
   # Edit .env and add your Google API key
   ```

## ⚙️ Configuration

Create a `.env` file in the project root with your API credentials:

```env
# Google Generative AI Configuration
GOOGLE_API_KEY=your_api_key_here

# Optional: Additional configurations
# MODEL_TEMPERATURE=0.7
# MAX_TOKENS=512
```

## 🎮 Quick Start

### Running the Baseline

```bash
jupyter notebook baseline_RAG.ipynb
```

The baseline pipeline implements:
- **Embedding Model**: `gemini-004` for semantic search
- **Generation Model**: `Gemini 2.5 Flash` for answer synthesis
- **Retrieval Strategy**: Dense retrieval with cosine similarity

### Exploring Improvements

```bash
jupyter notebook improved_RAG.ipynb
```

Enhanced features include:
- Hybrid retrieval strategies
- Query expansion techniques
- Context reranking mechanisms
- Prompt optimization

## 📊 Baseline RAG Performance


| Metric | mean_score | Std Dev | Description |
|--------|-------|---------|-------------|
| **Answer Faithfulness** | 0.98 | ±0.063 | Factual consistency with retrieved context |
| **Answer Relevancy** | 0.81 | ±0.341 | Direct answer to the query |
| **Context Precision** | 0.82 | ±0.114 | Relevance of retrieved documents |
| **Average Score** | 0.87 | ±0.141 | Overall RAG performance |

*Summary statistics were obtained by evaluating on `train.csv`. The full data can be found by running `baseline_RAG.ipynb`*

### 🚧 Problem analysis

 **Biggest problem** - Answer Relevancy's standard deviation is very high, and the minimum score is 0.

 **less urgent problem** - Context Precision has a relatively low score and standard deviation. 

### 🎯 What do these problems indicate?

**inconsistency in LLM answers** - 
The high standard deviation indicates that the LLM's ability to provide a relevant answer is unreliable. It can produce answers that are completely off-topic (min score of 0.0); we should try to make it more robust and stick to the context. 


**room to improve** - 
An average of 0.82 in Context Precision indicates that the documents being retrieved are generally relevant and useful for answering the question. But there is still room to improve the precision. And this improvement on Context precision can improve the Answer Relevancy score. 

So the place to look at is the `generate_answer`,`add_documents` and `retrieve` method. 

Detail improvement can be found on `improved_RAG` notebook.

## 📈 Improved RAG Performance

### Improvements Made:

- **Prompt**: A more robust prompt for context awareness to avoid hallucination.
- **Embedding**: Excluded titles from embeddings to improve retrieval precision.

## 📖 Documentation

### Dataset Information

- **Source**: [BEIR NFcorpus](https://huggingface.co/datasets/BeIR/nfcorpus)
- **Domain**: Nutrition and health queries
- **Size**: ~3.6K queries, ~3.6K documents
- **Characteristics**: Medical/nutrition focused, expert-annotated relevance

### Evaluation Framework

We use [RAGAS](https://github.com/explodinggradients/ragas) for comprehensive evaluation:

- **Faithfulness**: Ensures generated answers are grounded in retrieved context
- **Context Quality**: Measures precision and recall of retrieval
- **Answer Quality**: Assesses relevancy and completeness



## 🙏 Acknowledgments

- **BEIR Team** for the NFcorpus dataset
- **Google AI** for Gemini API access
- **RAGAS Team** for the evaluation framework
- **Community Contributors** for feedback and improvements

---

<div align="center">

**Made with ❤️ by Hao Shen**

[⬆ Back to Top](#-rag-on-nfcorpus)

</div>