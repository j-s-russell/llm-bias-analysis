# Analyzing LLM Sensitivity to User Self-Descriptions

This project investigates how large language models adapt their linguistic style based on user demographic characteristics provided in conversation context.

## Overview

Rather than examining responses to demographic-specific questions, this research focuses on how LLMs subtly adjust language features (sentiment, lexical diversity, politeness, and factual vs. opinionated language) when responding to general prompts from users with different self-described characteristics.

## Dataset

- **Models**: Grok 4.1 Fast, Gemini 2.0 Flash, Qwen Turbo
- **User Characteristics**: 
  - Age (15, 25, 50)
  - Gender (male, female, non-binary)
  - Religion (religious, atheist)
  - Political Affiliation (democrat, republican)
- **Total Responses**: 96,000 generated responses (100 tokens each)
- **Collection Method**: OpenRouter API with systematic sampling across models, prompts, temperatures, and user characteristics

## Key Findings

- **Model architecture** is the dominant factor in determining linguistic features
- **Religion** shows the strongest effect: religious users receive more positive sentiment and less fact-asserting language across all models
- **Political affiliation** triggers systematic differences: Republican users receive more factual language, while Democratic users receive more opinion-based language
- **Age and gender** show minimal systematic influence on most linguistic features
- **DistilBERT classifiers** successfully predict user characteristics from responses (up to 77% accuracy for religion), confirming that detectable linguistic patterns exist

## Methodology

### Linguistic Analysis
1. **Sentiment**: VADER compound scores
2. **Lexical Diversity**: Type-Token Ratio (TTR)
3. **Politeness**: Intel/polite-guard transformer classifier
4. **Factual vs. Opinionated**: Lexicon-based word counting approach

### Classification
- Fine-tuned DistilBERT models for each model-characteristic combination
- Single BERT model trained on all responses for SHAP analysis
- Validation accuracy ranges from 0.41-0.77 depending on characteristic and source model

## License

[Your chosen license]
