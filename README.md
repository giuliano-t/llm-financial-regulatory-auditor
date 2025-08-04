# LLM Financial Regulatory Auditor

This project implements an evaluation framework for **Agent 3**, a CLAUDE-based LLM agent developed as part of a collaborative research project involving the Bank of England.

The objective of the broader project was to develop a pipeline capable of extracting risk-relevant information from highly unstructured data — specifically, quarterly earnings call transcripts.

Agent 3 was originally developed by a colleague to extract structured insights, such as sentiment, risk indicators, and supervisory relevance, from earnings call transcripts, with particular focus on Q&A exchanges between analysts and executives.

**My contribution** focuses on designing a meta-evaluation pipeline that systematically reviews the outputs of **Agent 3**. The goal is to assess the relevance, justification, and overall usefulness of each extracted metric using a second LLM (e.g. OpenAI GPT-4o) acting as a regulatory "virtual supervisor".

---

##  Project Overview

- **Input:** Earnings call transcripts in thread format (Q&A or executive monologues)  
- **Agent 3 Output:** Structured JSONs with 50+ regulatory, conversational, and linguistic metrics  
- **Meta-Evaluation:** A second LLM reviews each output metric and recommends whether to Keep, Revise, or Remove it

---

![Agent3 Evaluation Pipeline](https://github.com/giuliano-t/llm-financial-regulatory-auditor/blob/main/Pipelines_Diagram.jpg?raw=true)

---

##  Key Features

- Thread-type classification and regulatory context injection using PRA 2025 priorities  
- Row-wise reconstruction of flattened `.csv` outputs into structured JSON  
- Context-aware meta prompts that enforce a strict evaluation format  
- Batch processing of LLM reviews using GPT-4o and aggregation of scoring patterns  
- Visualization of top/bottom performing metrics and common recommendations  

---

##  How to Use

1. **Open in Google Colab**  
   [Open the notebook in Colab](https://colab.research.google.com/github/giuliano-t/llm-financial-regulatory-auditor/blob/main/Agent3_Output_Assessment.ipynb)

2. **Install dependencies** in a notebook cell:
   ```python
   !pip install -q -r https://raw.githubusercontent.com/giuliano-t/llm-financial-regulatory-auditor/main/requirements.txt
3. **Set your OpenAI API key** (in a temporary private cell):

    ```
    import os
    os.environ["OPENAI_API_KEY"] = "sk-your-key-here"
    ```

4. **Run the notebook** to:
    - Load sample output data  
    - Generate meta-evaluation prompts  
    - Submit to GPT-4o  
    - Parse, analyze, and visualize relevance scores
