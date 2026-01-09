# Plane to See: Modeling How Toxicity and Emotions Take Off in Airline Conversations on Reddit

## Overview

This project introduces a computational linguistic framework that analyzes airline reputation through Reddit conversations, moving beyond traditional sentiment analysis to capture the structural dynamics of online discourse. By modeling Reddit's conversational structure as tree-based graphs, we analyze how toxicity and emotional content propagate through discussion hierarchies.

## Research Questions

1. **Conversational Structure**: How do discussions of Delta Airlines and Southwest Airlines differ in terms of breadth (participation) and depth (engagement) on Reddit?

2. **Thematic Focus**: What specific operational themes serve as high-risk vectors for generating toxic discourse for each carrier?

3. **Strategic Insights**: How can analysis of community reactions to toxic content inform strategic reputation management?

## Methodology

### Data Collection
- **Source**: Reddit subreddits for Delta Airlines and Southwest Airlines
- **Volume**: 15,369 Reddit comments (6,413 Delta, 8,956 Southwest)
- **Tool**: PRAW (Python Reddit API Wrapper)
- **Structure**: Preserved hierarchical parent-child relationships for tree-based analysis

### Models Used

1. **Emotion Classification**
   - **Model**: RoBERTa-base fine-tuned on dair-ai/emotion dataset
   - **Classes**: 6 emotions (sadness, joy, love, anger, fear, surprise)
   - **Performance**: 92.65% accuracy

2. **Toxicity Detection**
   - **Model**: DeBERTa-v3-base fine-tuned on ToxiGen dataset
   - **Classes**: 5 toxicity levels (non-toxic to severe)
   - **Performance**: 42.8% balanced accuracy (2.1× above random)

3. **Topic Modeling**
   - **Framework**: BERTopic with UMAP + HDBSCAN clustering
   - **Output**: 30 distinct thematic clusters (21 airline-related)

## Key Findings

### Overall Results
- **Emotional Baseline**: 61% positive sentiment across both airlines
- **Toxicity Distribution**: 93.2% non-toxic/mild content
- **Community Behavior**: Remarkably similar patterns between Delta and Southwest

### High-Risk Topics
Topics with elevated toxicity and anger probability:
1. **Moderation** (+3.78pp toxicity risk)
2. **Cleanliness** (+2.89pp toxicity risk)
3. **Diversity** (+2.27pp toxicity risk)
4. **Legal Issues** (+2.16pp toxicity risk)

### Airline Comparison
- **Delta**: Higher mean toxicity (1.68 vs 1.54) and anger prevalence (38.5% vs 31.2%)
- **Southwest**: More non-toxic content and higher community engagement scores

## Practical Implications

1. **Resource Allocation**: Focus moderation efforts on high-risk topics (Cleanliness, Moderation, Legal, Diversity)
2. **Early Warning Systems**: Use anger detection as a leading indicator for toxic content
3. **Community Benchmarking**: Delta-Southwest differential provides evaluation metrics for interventions

## Repository Structure
```
plane2see/
├── data/
│   ├── raw/                    # Raw scraped Reddit data
│   └── processed/              # Cleaned and preprocessed datasets
├── models/
│   ├── emotion/               # Emotion classification model artifacts
│   ├── toxicity/              # Toxicity detection model artifacts
│   └── topic/                 # Topic modeling outputs
├── notebooks/
│   ├── data_collection.ipynb  # Reddit scraping and preprocessing
│   ├── emotion_analysis.ipynb # Emotion classification pipeline
│   ├── toxicity_analysis.ipynb# Toxicity detection pipeline
│   └── topic_modeling.ipynb   # Topic discovery and analysis
├── src/
│   ├── data_processing/       # Data cleaning and preparation scripts
│   ├── modeling/              # Model training and inference
│   └── visualization/         # Analysis and visualization tools
└── results/
    ├── figures/               # Generated plots and visualizations
    └── reports/               # Final analysis reports
```

## Installation & Usage

### Requirements
```bash
pip install -r requirements.txt
```

### Key Dependencies
- `praw` - Reddit API wrapper
- `transformers` - Hugging Face transformer models
- `bertopic` - Topic modeling framework
- `scikit-learn` - Machine learning utilities
- `pandas`, `numpy` - Data manipulation
- `matplotlib`, `seaborn` - Visualization

### Quick Start
1. Clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Configure Reddit API credentials in `config.py`
4. Run data collection: `python src/data_collection/reddit_scraper.py`
5. Execute analysis notebooks in sequence

## Results Summary

| Metric | Delta Airlines | Southwest Airlines |
|--------|----------------|-------------------|
| Mean Toxicity | 1.68 | 1.54 |
| High Toxicity Rate | 3.2% | 2.4% |
| Anger Prevalence | 38.5% | 31.2% |
| Positive Sentiment | 61.2% | 60.9% |

## Team

- **Kenneth L. Molina** - Phd Data Science Student - School of Statistics
- **Robert Cruz** - Phd Data Science Student - School of Statistics 
- **Yves Kangleon** - Phd Data Science Student - School of Statistics

**Course**: DS 397 Natural Language Processing  
**Instructor**: Dr. Miguel Remolona  
**Institution**: University of the Philippines Diliman  
**Semester**: 1st Semester, AY 2025-2026

## Citation
```bibtex
@article{molina2025plane2see,
  title={Plane to See: Modeling How Toxicity and Emotions Take Off in Airline Conversations on Reddit},
  author={Molina, Kenneth L. and Cruz, Robert and Kangleon, Yves},
  journal={DS 397 Natural Language Processing},
  year={2025},
  institution={University of the Philippines Diliman}
}
```

## Acknowledgments

- **Dr. Miguel Remolona** - Class adviser and professor for DS 397 Natural Language Processing, for his invaluable guidance, mentorship, and support throughout this project
- University of the Philippines Diliman School of Statistics
- Reddit API for data access
- Hugging Face for pre-trained transformer models
- The open-source NLP community for foundational research
- Our fellow classmates in DS 397 for their feedback and collaborative discussions
