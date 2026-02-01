[README.md](https://github.com/user-attachments/files/24972284/README.md)
# 20th Century Timeline Analysis

## Overview

This repository contains a comprehensive text mining and sentiment analysis project examining historical events from the 20th century. The project demonstrates end-to-end data science capabilities including web scraping, natural language processing, statistical analysis, and data visualization using Python.

## Project Scope

This analysis showcases proficiency in:
- Automated web scraping and data extraction
- Natural language processing and computational linguistics
- Statistical analysis and feature engineering
- Data visualization and insight generation
- Sentiment analysis using machine learning techniques

## Repository Structure

```
20th-century-project/
├── 20th_century_scrape.ipynb      # Web scraping implementation
├── 20th_century_text_mining.ipynb # Text mining and NLP analysis
├── 20th_century_events.txt        # Extracted Wikipedia dataset
├── countries_scrape.ipynb         # Supplementary entity extraction
├── countries_list.txt             # Reference dataset (373 entities)
└── README.md                      # Documentation
```

## Technical Implementation

### Exercise 1.4: Web Scraping

#### Objective
Extract and persist structured text data from Wikipedia's Timeline of the 20th Century for subsequent analysis.

#### Implementation Details

**Primary Data Extraction**
- Source: [Wikipedia - Timeline of the 20th century](https://en.wikipedia.org/wiki/Timeline_of_the_20th_century)
- Technology Stack: BeautifulSoup4, Python Requests library
- Dataset Size: 101,768 characters
- Compliance: User-agent headers implemented per Wikipedia's robots.txt policy

**Supplementary Entity Extraction**
- Source: [Wikipedia - List of countries](https://simple.wikipedia.org/wiki/List_of_countries)
- Technology Stack: Selenium WebDriver, ChromeDriver
- Output: Reference list of 373 sovereign entities
- Purpose: Named entity resolution for geographical analysis

### Exercise 1.5: Text Mining and Sentiment Analysis

#### Objective
Perform comprehensive natural language processing analysis on the extracted historical dataset to identify patterns, key entities, and sentiment trends.

#### Analysis Pipeline

**1. Tokenization and Lexical Analysis**
- Processed 19,032 tokens from the source text
- Implemented stop word filtering using NLTK corpus
- Applied frequency distribution analysis pre and post-filtering
- Key findings: "war" (151 occurrences), "first" (171 occurrences), "begins" (115 occurrences)

**2. Part-of-Speech Tagging and Grammatical Analysis**
- Tagged 15,966 lexical units using TextBlob POS tagger
- Distribution analysis:
  - Proper nouns (NNP): 5,552 instances (34.8%)
  - Common nouns (NN): 1,847 instances (11.6%)
  - Cardinal numbers (CD): 1,705 instances (10.7%)
- Insight: High proper noun density characteristic of historical documentation

**3. Semantic Category Extraction**

Top 15 entities by grammatical category:

| Category | Top Terms |
|----------|-----------|
| Nouns | War, United, March, October, May, September |
| Verbs | is, begins, becomes, ends, founded, killing |
| Adjectives | first, British, military, German, Soviet, Russian |

**4. Named Entity Recognition - Geographical Analysis**
- Analyzed 373 country entities against the corpus
- Detection rate: 154 entities (41.3% coverage)
- Geographic distribution (top 5 by mention frequency):

| Rank | Entity | Frequency |
|------|--------|-----------|
| 1 | United States | 55 |
| 2 | Israel | 35 |
| 3 | China | 34 |
| 4 | Russia | 30 |
| 5 | Japan | 29 |

**5. Sentiment Analysis Using Machine Learning**

Implemented TextBlob's pre-trained sentiment classifier on 1,046 sentences.

*Aggregate Metrics:*
- Polarity Score: 0.087 (slightly positive, normalized scale: -1 to +1)
- Subjectivity Score: 0.285 (objective-leaning, scale: 0 to 1)

*Distribution Analysis:*
- Neutral sentences: 766 (73.2%)
- Positive sentences: 229 (21.9%)
- Negative sentences: 51 (4.9%)

*Statistical Summary:*
- Mean polarity: 0.043
- Median polarity: 0.000 (neutral baseline)
- Mean subjectivity: 0.138 (highly objective)

**Key Insight:** The corpus maintains strong editorial neutrality (mean subjectivity: 0.138), consistent with encyclopedic standards for historical documentation.

## Technology Stack

**Core Environment**
- Python 3.11.14
- Conda environment management

**Libraries and Frameworks**

| Library | Version | Purpose |
|---------|---------|---------|
| beautifulsoup4 | 4.12.2 | HTML/XML parsing |
| requests | 2.31.0 | HTTP client |
| selenium | 4.15.0 | Browser automation |
| nltk | 3.7 | Natural language toolkit |
| textblob | 0.17.1 | Sentiment analysis |
| pandas | 1.5.1 | Data manipulation |
| numpy | 1.23.5 | Numerical computing |
| matplotlib | 3.6.2 | Visualization |
| seaborn | 0.12.1 | Statistical visualization |

## Visualizations and Outputs

The analysis generates multiple data visualizations:
- Frequency distribution plots (pre/post stop-word removal)
- Part-of-speech tag distribution analysis
- Categorical word frequency charts (nouns, verbs, adjectives)
- Geographical entity mention analysis (horizontal bar chart)
- Sentiment distribution histograms (polarity and subjectivity)

## Setup and Execution

### Environment Configuration

```bash
# Create isolated Python environment
conda create -n 20th_century python=3.11

# Activate environment
conda activate 20th_century

# Install dependencies
pip install beautifulsoup4==4.12.2 requests==2.31.0 selenium==4.15.0
pip install nltk==3.7 textblob==0.17.1
pip install pandas==1.5.1 numpy==1.23.5
pip install matplotlib==3.6.2 seaborn==0.12.1

# Download NLTK data packages
python -c "import nltk; nltk.download('stopwords'); nltk.download('punkt'); nltk.download('averaged_perceptron_tagger')"
```

### Running the Analysis

```bash
# Launch JupyterLab with increased data rate limit
jupyter lab --NotebookApp.iopub_data_rate_limit=10000000

# Execute notebooks in sequence:
# 1. 20th_century_scrape.ipynb - Data extraction
# 2. 20th_century_text_mining.ipynb - NLP analysis
```

## Results and Insights

### Key Findings

1. **Lexical Analysis**
   - Stop word removal increased signal-to-noise ratio by 46.8% (19,032 → 10,134 meaningful tokens)
   - "War" emerged as the dominant semantic theme (151 occurrences)

2. **Grammatical Structure**
   - Proper noun density (34.8%) indicates event-driven narrative structure
   - Cardinal number frequency (10.7%) reflects chronological organization
   - Temporal markers (month names) show strong presence in top nouns

3. **Geopolitical Analysis**
   - Coverage of 154 sovereign entities (41.3% of global nations)
   - Western and East Asian regions show higher mention density
   - United States mentioned 1.6x more frequently than next entity

4. **Sentiment Characteristics**
   - Near-neutral median polarity (0.000) validates encyclopedic neutrality
   - 73.2% neutral classification demonstrates minimal editorial bias
   - Low subjectivity score (0.138) appropriate for historical documentation

### Technical Insights

1. **Web Scraping Best Practices**
   - User-agent headers essential for compliance with robots.txt
   - BeautifulSoup optimal for static content extraction
   - Selenium necessary for JavaScript-rendered elements

2. **NLP Pipeline Optimization**
   - Stop word filtering significantly improves semantic analysis
   - POS tagging reveals document structure and content type
   - Proper noun extraction effective for entity identification

3. **Data Quality Assessment**
   - Wikipedia maintains consistent editorial standards (subjectivity: 0.138)
   - Temporal bias evident in chronological event distribution
   - Geographical bias reflects historical Western documentation patterns

## Author

**Saurabh Singh**  
Product Manager

## Project Information

- **Completion Date:** January 30, 2026
- **Program:** CareerFoundry Data Visualization with Python Specialization
- **Exercises Completed:** 1.4 (Web Scraping), 1.5 (Text Mining and Sentiment Analysis)

## Acknowledgments

This project utilizes open-source tools and datasets:
- Wikipedia for historical data access
- NLTK team for natural language processing infrastructure
- TextBlob developers for sentiment analysis implementation
- CareerFoundry for curriculum design and project framework

## License

This project is developed for educational purposes as part of professional training in data science and analytics.
