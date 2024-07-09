# Data Transformation

After the news data ingestion, the required columns need to be extracted from the raw JSON files and written into delta tables. For all the necessary data transformations, Synapse Data Engineering component of Fabric is used.
- To start using the notebook, navigate to Synapse Data Engineering Component -> Notebook -> Lakehouse -> Add -> Existing Lakehouse -> 
  choose the lakehouse in which data is ingested (bing_lake_db)
- The data transformation part of the project is executed through the [process_bing_news.ipynb](/03_Data%20Transformation/process_bing_news.ipynb) 
  notebook 
- Initially when the raw data is read into a dataframe from the files, it contains these columns: ['_type', 'queryContext', 'readLink', 'sort', 
  'totalEstimatedMatches', 'value']
- The 'value' column has the json objects of the file as one single row, which will be selected to get the following data about each news article:
   - title
   - description
   - category
   - image
   - provider
   - datePublished
- Since news articles are not updated after release, tracking the history of updates is unnecessary. Therefore, Type 1 incremental loading is 
  best suited for this scenario, and this approach is implemented in the notebook.The cleaned, structured data is loaded into a delta table of 
  the lakehouse.

