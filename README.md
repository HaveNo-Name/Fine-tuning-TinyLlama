# Fine-tuning-TinyLlama

This project is a comprehensive evaluation of different fine-tuning strategies for legal document summarization using the **TinyLlama-1.1B** model on the Indian Legal Document dataset. We investigated four distinct approaches:

1. **Freezing all layers except the output layer**
2. **Freezing 80% of layers with selective training**
3. **Low-Rank Adaptation (LoRA)**
4. **Quantized LoRA (QLoRA)**


### Dataset Description

* **Dataset:** Indian Legal (IN-Ext) corpus, (IN-Abs)
* **Total Available Data:** ~7,000 judgment-summary pairs
* **Training Subset:** 500 randomly sampled pairs
* **Test Set:** 100 samples for evaluation
* **Summary Authors:** Two independent annotators (A1, A2)

### Model

* **Model:** `TinyLlama/TinyLlama-1.1B-Chat-v1.0`
* **Parameters:** 1.1 billion
* **Architecture:** Transformer-based causal language model
* **Context Window:** 2048 tokens
* **Input Token Limit:** 1536 tokens (allowing 512 for generation)

---

### Results and Analysis

| **Method**               | **Inference Time (s)** | **ROUGE-1** | **ROUGE-2** | **ROUGE-L** | **ROUGE-Lsum** |
| ------------------------ | ---------------------: | ----------: | ----------: | ----------: | -------------: |
| **LoRA**                 |                 133.75 |      0.3469 |      0.0858 |      0.1819 |         0.3182 |
| **QLoRA**                |                  76.15 |      0.3427 |      0.0851 |      0.1900 |         0.3130 |
| **Freeze Last Layer**    |                 735.97 |      0.3216 |      0.0843 |      0.1721 |         0.2972 |
| **Freeze 80% of layers** |                 648.32 |      0.3597 |      0.1004 |      0.1796 |         0.3348 |

