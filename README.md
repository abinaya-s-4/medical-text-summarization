# Medical Text Summarization Using BART with LoRA-Based Parameter-Efficient Fine-Tuning

This repository presents an academic implementation of medical text summarization using the BART transformer model fine-tuned with Low-Rank Adaptation (LoRA), a Parameter-Efficient Fine-Tuning (PEFT) technique. The project is intended for research, experimentation, and pedagogical use in the domain of Medical Natural Language Processing (NLP).

---

## Research Motivation

Medical literature is extensive, technical, and continually growing. Extracting concise and accurate summaries from lengthy medical documents is challenging due to:

- specialized biomedical terminology  
- complex sentence structures  
- contextual dependencies across long documents  
- the need for high factual precision  

This project addresses these challenges through the use of BART with LoRA adapters, allowing efficient fine-tuning without sacrificing performance.

---

## Methodology

### 1. Model Architecture

- **Base Model:** BART (Bidirectional and Auto-Regressive Transformers)  
- **Adaptation Method:** Low-Rank Adaptation (LoRA) applied to attention layers  
- **Parameter Efficiency:** Only ~0.018% of parameters are updated  
- **Outcome:** Reduced compute cost and memory usage with stable training  

---

### 2. Dataset

- Source: PubMed medical abstracts and article texts  
- Preprocessing Includes:
  - text cleaning and normalization  
  - removal of formatting artifacts  
  - tokenization using BART tokenizer  
  - truncation and padding as required  

---

### 3. Training Workflow

The fine-tuning process (shown in `finetuned_model.ipynb`) uses:

- Hugging Face Transformers  
- PEFT + LoRA integration  
- Adam optimizer  
- Cross-entropy loss  
- Gradient clipping  
- Early stopping for stability and overfitting control  

Training was conducted in Jupyter Notebook, allowing detailed incremental debugging and visualization of intermediate outputs.

---

### 4. Inference Workflow

The `generate_summary.ipynb` notebook demonstrates:

- Loading the fine-tuned BART-LoRA model  
- Tokenizing raw medical input  
- Generating summaries using autoregressive decoding (`model.generate()`)  
- Converting model outputs into readable summaries  

---

## Getting Started

### 1. Clone the repository

```bash
git clone <https://github.com/abinaya-s-4/medical-text-summarization>
cd medical-text-summarization-project
```

---

## Python Environment Setup

### 2. Create a virtual environment (optional)

```bash
python -m venv venv
source venv/bin/activate
```

Windows:

```bash
venv\Scripts\activate
```

---

## Install Dependencies

### 3. Install required libraries

```bash
pip install -r requirements.txt
```

---

## Training

### 4. Execute the training script

```bash
python train.py --config config.yaml
```

Alternatively, training can be run interactively inside the notebook `finetuned_model.ipynb`.

---

## Inference

To run inference:

1. Load the model and tokenizer in `generate_summary.ipynb`  
2. Tokenize input medical text  
3. Generate summaries using:

```
model.generate()
```

4. Decode token IDs to readable text  
5. View results in notebook output cells  

---

## Notes

- This project is **not deployed** as an API or application.  
- Evaluation is primarily qualitative with limited automated metrics.  
- LoRA was essential to enable fine-tuning on limited hardware resources.  
- The work is intended for research, learning, and experimentation.

---

## Future Work

- Integration of ROUGE/BERTScore evaluation  
- Exploration of domain-specific pretrained models (BioBART, BioGPT, PubMedBERT)  
- Building an interactive web interface for demonstration  
- Experiments with RL-based summarization methods (RLHF, RLAIF)

---




