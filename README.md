# AI-Powered Environmental Health Literature Extraction Pipeline

Automated extraction of environmental exposures and health outcomes from scientific literature using a structured 3-layer taxonomy and large language models.

---

## 1. Business Problem

Environmental health research often requires reviewing large volumes of scientific literature to identify how different exposures (such as air pollution, heavy metals, or diet) influence human health outcomes like cardiovascular or respiratory diseases.

This process is typically manual, time-consuming, and difficult to scale.

The goal of this project is to develop an automated approach that extracts these relationships directly from research papers using AI, allowing for faster and more consistent analysis.

---

## 2. Project Overview

| Component | Description |
|----------|------------|
| Objective | Extract exposure–outcome relationships from scientific literature |
| Method | LLM-based extraction guided by a 3-layer taxonomy |
| Models | GPT-3.5 (baseline), GPT-4o (advanced) |
| Evaluation Data | 86 papers (Phase 4), 121 papers (Phase 5) |
| Best Result | F1 score above 96% at Layer 1 |
| Coverage | 100% of papers successfully processed |

---

## 3. Data

### Ground Truth Dataset
- Source: VA Normative Aging Study  
- File: `CohortNetwork_ES&T_SI_B_Main.xlsx`  
- Description: Expert-annotated exposure–outcome relationships  
- Size: 428 labeled pairs across 121 papers  

### Research Papers Dataset
- File: `output_11.csv`  
- Description: Collection of scientific articles used as input  

### Taxonomy
- Structured into 3 hierarchical levels  
- Contains over 100 detailed exposure and outcome categories  

---

## 4. Data Preprocessing

- Retrieved abstracts using PubMed and related sources  
- Identified and collected full-text documents  
- Extracted content from PDFs  
- Cleaned and standardized text data  
- Prepared structured input for model processing  

---

## 5. Exploratory Data Analysis

Key observations:

- Most studies focus on air pollution and heavy metal exposure  
- Cardiovascular and respiratory outcomes appear most frequently  
- Fewer observations are available in deeper taxonomy levels  

---

## 6. Modeling Approach

### Baseline Model (GPT-3.5)
- Uses abstracts only  
- Faster and more cost-efficient  
- Limited by reduced context  

### Advanced Model (GPT-4o)
- Uses full-text documents  
- Provides richer context and improved accuracy  
- Higher computational cost  

---

## 7. Model Comparison

| Model   | Input Type | Strengths        | Limitations       | Performance |
|--------|-----------|------------------|------------------|------------|
| GPT-3.5 | Abstracts | Fast, low cost   | Limited context   | ~61% accuracy |
| GPT-4o  | Full Text | More accurate    | Higher cost       | 96%+ F1 score |

---

## 8. Model Training

- Prompt design based on taxonomy categories  
- Low temperature for consistent outputs  
- Semantic matching used to evaluate predictions  
- Similarity threshold applied (~0.75)  

---

## 9. Results

### Phase 4 (Validation)

- Conducted on 86 papers using abstracts  
- Achieved ~61% accuracy at Layer 1  
- Performance decreased for deeper classification levels  
- Main limitation: incomplete context from abstracts  

---

### Phase 5 (Full Pipeline)

- Applied to 121 full-text papers  
- 100% of papers processed successfully  
- Improved extraction quality compared to Phase 4  
- Semantic matching significantly improved evaluation results  

---

### Performance Summary

| Setup              | Input Type | Observation |
|------------------|-----------|------------|
| Phase 4          | Abstracts | Moderate performance due to limited context |
| Phase 5          | Full Text | Improved accuracy with richer information |
| Semantic Matching | Full Text | Best performance by handling wording variations |

---

### Example Output

| Paper ID | Exposure        | Outcome                     |
|----------|---------------|----------------------------|
| 001      | Air Pollution | Cardiovascular Disease     |
| 002      | Lead Exposure | Cognitive Decline          |
| 003      | Diet          | Obesity                    |

---

### Output Files

- `Phase5_extraction_results.csv`  
- `Phase5_extraction_results_metrics.csv`  
- `Phase5_extraction_results_with_strategies.csv`  
- `Phase5_extraction_results_with_strategies_metrics.csv`  
- `aggressive_semantic_extraction_*.csv`  

These files contain extracted relationships, evaluation metrics, and comparisons across different extraction strategies.

---

### Visual Results

(Add your screenshots in an `images/` folder)

![Example Output](images/output_example.png)
![Performance](images/performance.png)

---

## 10. Model Interpretation

Model predictions are influenced by:

- Similarity between text and taxonomy categories  
- Presence of key exposure and outcome terms  
- Context within full-text documents  

### Strengths
- Performs well when terminology is clearly stated  
- Can extract multiple relationships from a single paper  

### Limitations
- Sensitive to wording differences  
- More difficult to detect implicit relationships  

---

## 11. Key Insights

- Taxonomy-guided prompts improve consistency  
- Full-text input significantly increases performance  
- Evaluation method impacts reported accuracy  
- Automation reduces analysis time from hours to minutes  

---

## 12. Conclusion

This project demonstrates that large language models can effectively automate the extraction of structured information from environmental health literature.

The approach is scalable and can support large-scale research analysis.

---

## 13. Future Work

- Improve handling of synonyms and variations  
- Expand dataset size  
- Introduce confidence scoring  
- Develop a user interface  

---

## 14. How to Run

```bash
pip install -r requirements.txt
