## RAG on NFcorpus

### Overview
This project aims to improve Retrieval-Augmented Generation (RAG) performance on the BEIR/NFcorpus dataset. It includes a simple baseline and an improved variant, with evaluation via RAGAS.

### Dataset
- **Source**: BEIR NFcorpus
- **Prepared files**: see `assets/` for `train.csv`, `validation.csv`, `test.csv`, `corpus.csv`, `queries.csv`.

### Project structure
- `baseline_RAG.ipynb`: baseline RAG pipeline and evaluation
- `improved_RAG.ipynb`: experiments with improved RAG
- `get_corpus.ipynb`, `get_query.ipynb`, `get_qrels.ipynb`: data preparation
- `assets/`: preprocessed CSVs

### Setup
- **Python**: 3.9+
- Create a virtual environment and install dependencies:
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
pip install -U google-generativeai ragas pandas numpy scikit-learn jupyter python-dotenv
```

### Environment
Set your Google Generative AI API key in `.env`:
```bash
GOOGLE_API_KEY=your_api_key_here
```

### Baseline model
The baseline is a minimal RAG system:
- **Embedding model**: `gemini-004`
- **Answering model**: `Gemini 2.5 Flash`

**RAGAS performance**: as the summary statistics show in `baseline_RAG.ipynb`.

### How to run
1. Ensure dependencies are installed and `GOOGLE_API_KEY` is set.
2. Open `baseline_RAG.ipynb` and run all cells to reproduce the baseline.
3. Open `improved_RAG.ipynb` to explore improvements.

### Evaluation
RAG quality is measured with RAGAS (e.g., answer faithfulness, context precision/recall, answer relevancy). See the notebook outputs for metric tables and summary statistics.

### License
See `LICENSE` for details.
