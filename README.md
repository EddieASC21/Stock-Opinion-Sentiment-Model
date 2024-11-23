# Stock Opinion Sentiment Model

## Overview
The StockSentiment Analysis Tool is developed for the Cornell Fintech Club as part of the stocksentiment project. This tool is designed to provide sentiment scores for selected stocks based on the latest news articles, utilizing advanced data processing techniques with Spark and Spark NLP.

## Inspiration
This project is inspired by Duke Pan's `WallStreetBets_BigDataAnalysis`, available [here](https://github.com/Fryingpannn/WallStreetBets_BigDataAnalysis). While Duke Pan's project provides a broad analysis of market sentiments, this tool specifically analyzes sentiment by fetching news articles via the TickerTick API for a pre-defined list of stock tickers, making the analysis more direct and user-focused.

## Repository
This tool is part of the [stocks sentiment project](https://github.com/Cornell-Fintech-Club/stocksentiment) hosted on the Cornell Fintech Club's GitHub.

## Setup

### Prerequisites
Ensure you have Python installed with the following packages:
- pyspark
- spark-nlp

### Installation
Install the necessary packages:
```bash
!pip install pyspark
!pip install spark-nlp
```

## Why These Libraries?

### pyspark
**PySpark** is the Python API for Spark, an immensely powerful analytics engine, which allows for large-scale data processing and analytics. We use PySpark to handle distributed data processing efficiently, enabling our tool to analyze large volumes of news data quickly and scale as needed.

### spark-nlp
**Spark NLP** is a natural language processing library built on top of Apache Spark and Spark ML. It provides simple, performant & accurate NLP annotations for machine learning pipelines, which allow us to process and analyze large datasets of textual information efficiently. This library supports our need to implement complex NLP tasks like tokenization, normalization, and sentiment analysis seamlessly integrated within the Spark ecosystem.

## How the Code Works
The tool operates by following a streamlined process:

1. **Data Fetching:** The script uses the TickerTick API to fetch the latest news articles associated with given stock tickers. This ensures that the sentiment analysis is based on the most recent market news.

2. **Data Processing:**
   - **Document Assembling:** Each news article text is converted into a document format suitable for NLP operations.
   - **Tokenization and Normalization:** The text is split into tokens or words, and these tokens are normalized to lower cases, stripped of punctuations to ensure uniformity.
   - **Stop Words Removal:** Common words that add no significant value to sentiment analysis are removed.
   - **Lemmatization:** Words are reduced to their base or root form, enhancing the analysis's effectiveness by grouping similar forms of the same word.

3. **Feature Engineering:**
   - **TF-IDF:** The tool converts the processed text into a numerical format using the Term Frequency-Inverse Document Frequency (TF-IDF) method, which reflects how important a word is to a document in a collection or corpus.

4. **Model Training and Evaluation:**
   - A Naive Bayes classifier is used for predicting the sentiment as it is effective in classification based on word frequencies.
   - The model is trained with labeled data (if available) or uses previously determined sentiment scores as labels.

5. **Sentiment Scoring:** Each article's sentiment is evaluated, and an overall sentiment score for the stock is calculated based on the compiled sentiment values from all fetched articles.

6. **User Interaction:** The user inputs a stock ticker, and the tool outputs a sentiment score, providing insight into the general market sentiment surrounding that stock.

## Running the Tool
After installation, the script can be run directly in a Python environment that supports Spark. Here’s how to use the tool:

## Running the Tool
After installation, the script can be run directly in a Python environment that supports Spark. Here’s how to use the tool:

### Execution
1. Start the Python script provided in the repository.
2. The script will automatically ask you to input a stock ticker from the following list:
   ```plaintext
   ["AAPL", "MSFT", "AMZN", "GOOGL", "TSLA"]
3. Input the ticker you are interested in when prompted.
4. The tool will then fetch the 10 latest news articles related to the ticker and provide a sentiment score.

## Functionality
- **Data Fetching:** Automatically retrieves news articles related to the input stock ticker.
- **Sentiment Analysis:** Processes the text data from articles to determine the overall sentiment expressed about the stock.
- **User Interaction:** Simple user input to select the stock ticker from a predefined list, making it user-friendly.

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details.