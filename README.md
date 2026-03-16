# Extracting Key Themes from Evaluation Reports and Preparing an Automated Summary

## 📖 Overview
This project provides a pipeline for **automated content analysis** of evaluation reports. It extracts paragraphs from PDF documents, classifies them into predefined taxonomy categories, and generates structured outputs (Excel, Markdown, and Word summaries). The workflow leverages **LLM-powered classification** and summarization to produce actionable insights across child protection evaluation themes.

---

## ⚙️ Features
- **Taxonomy-driven classification**  
  - Loads a taxonomy from Excel (`library/taxonomy.xlsx`)  
  - Classifies paragraphs into relevant categories using an LLM  
  - Caches results for efficiency  

- **Paragraph extraction**  
  - Splits PDF text into ~5-sentence chunks  
  - Cleans and normalizes text for consistent processing  

- **Automated outputs**  
  - Excel file (`docs/classified_output_multicategory.xlsx`) with structured rows  
  - Markdown table (`docs/classified_output_multicategory.md`) for quick review  
  - Word document (`docs/summary_report.docx`) with professional summaries  

- **Summarization**  
  - Groups extracted content by category  
  - Produces a structured summary with **Introduction, Category-wise analysis, and Conclusion**  
  - Highlights strengths, weaknesses, recurring themes, and recommendations  

---

## 📂 Project Structure

├── library/
│   └── taxonomy.xlsx                  # Taxonomy definitions (Category, Description)
├── reports/
│   └── test_short.pdf                 # Example input report
├── docs/
│   ├── classified_output_multicategory.xlsx  # Classified results (Excel)
│   ├── classified_output_multicategory.md    # Classified results (Markdown table)
│   └── summary_report.docx            # Generated summary report (Word)
├── main.py                            # Core script for extraction & classification
├── summarize.py                       # Script for generating Word summary report
└── README.md                          # Project documentation

## 🚀 Usage

### 1. Install dependencies
```bash
pip install -r requirements.txt
````

Dependencies include:
- pandas
- pdfplumber
- ollama
- tqdm
- diskcache
- python-docx

### 2. Prepare taxonomy
Create an Excel file (library/taxonomy.xlsx) with the following columns:
- Category: Name of the category
- Description: Short description of the category

````bash
python main.py
````

This will:

- Read the input PDF (reports/test_short.pdf)
- Extract and classify paragraphs
- Save results to Excel and Markdown in docs/

### 3. Run classification
````bash
python main.py
````

This will:
- Read the input PDF (reports/test_short.pdf)
- Extract and classify paragraphs
- Save results to Excel and Markdown in docs/

### 4. Generate summary report

This will produce a Word document (docs/summary_report.docx) with:
- Introduction
- Category-wise summaries
- Conclusion

# 🧩 Example Output

## Markdown Table
| File name      | Category            | Extracted paragraph (verbatim) | ¶ / page / line reference |
|----------------|---------------------|--------------------------------|----------------------------|
| test_short.pdf | Case Management     | The evaluation found...        | [p.2]                      |
| test_short.pdf | Child Participation | Children reported...           | [p.3]                      |

---

## Word Summary Report
- **Introduction**: Purpose and scope of the evaluation  
- **Category Summaries**: Analytical synthesis per category  
- **Conclusion**: Cross-cutting findings and recommendations  

---

## 📌 Notes
- The classification relies on **LLM inference via Ollama**. Ensure the model (`mistral` or other) is available locally.  
- Caching is implemented to avoid redundant classification runs.  
- Summarization prompt enforces a professional, neutral tone with structured sections.  

---

## 🏆 Contribution
Contributions are welcome!  
- Extend taxonomy definitions  
- Improve summarization prompts  
- Add support for additional output formats  

---

## 📜 License
This project is released under the MIT License. See `LICENSE` for details.


