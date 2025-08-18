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

## 📊 Results

### Baseline Performance

| Metric | Score | Description |
|--------|-------|-------------|
| **Answer Faithfulness** | 0.XX | Factual consistency with retrieved context |
| **Context Precision** | 0.XX | Relevance of retrieved documents |
| **Context Recall** | 0.XX | Coverage of relevant information |
| **Answer Relevancy** | 0.XX | Direct answer to the query |

*Full evaluation metrics and detailed analysis available in `baseline_RAG.ipynb`*

### Enhanced Model Performance

🚧 **Coming Soon** - Check `improved_RAG.ipynb` for latest experiments

## 📖 Documentation

### Dataset Information

- **Source**: [BEIR NFcorpus](https://github.com/beir-cellar/beir)
- **Domain**: Nutrition and health queries
- **Size**: ~3.6K queries, ~3.6K documents
- **Characteristics**: Medical/nutrition focused, expert-annotated relevance

### Evaluation Framework

We use [RAGAS](https://github.com/explodinggradients/ragas) for comprehensive evaluation:

- **Faithfulness**: Ensures generated answers are grounded in retrieved context
- **Context Quality**: Measures precision and recall of retrieval
- **Answer Quality**: Assesses relevancy and completeness

## 🤝 Contributing

We welcome contributions! Please feel free to:

- 🐛 Report bugs
- 💡 Suggest new features
- 🔧 Submit pull requests
- 📚 Improve documentation

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **BEIR Team** for the NFcorpus dataset
- **Google AI** for Gemini API access
- **RAGAS Team** for the evaluation framework
- **Community Contributors** for feedback and improvements

---

<div align="center">

**Made with ❤️ by the RAG Research Team**

[⬆ Back to Top](#-rag-on-nfcorpus)

</div>