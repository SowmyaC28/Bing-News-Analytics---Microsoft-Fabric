# Sentiment Analysis using Synapse Data Science in Microsoft Fabric:

To proceed with analyzing text, Synapse Data Science component of Fabric is used as follows:
- Navigate to Synapse Data Science > Notebook, then create a new notebook by providing a name.
- Connect to the lakehouse:
    - Click on Lakehouses > Add > Existing Lakehouse > Add and select bing_lake_db (created during the Environment Setup stage).
- The notebook [news_sentiment_analysis.ipynb](/04_Sentiment%20Analysis/news_sentiment_analysis.ipynb)  contains PySpark code to run a 
  machine learning model that analyzes the news descriptions, identifying their sentiment as either 'negative', 'neutral', or 'positive'.
- In the notebook, a prebuilt intelligent model from SynapseML, AnalyzeText, is configured to analyze the news text from the description 
  column of the DataFrame.
- The news data, along with its corresponding sentiment value, is written to a delta table in the lakehouse. The logic for incremental 
  loading is implemented similar to the data transformation phase.
   
