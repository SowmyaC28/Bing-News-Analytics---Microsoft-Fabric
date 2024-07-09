# Data Ingestion

To ingest data, first a connection needs to be established between the API and Fabric Workspace. Later, Fabric needs to be provided the authentication to access the data through this connection. To achieve this:

- Navigate to the Data Factory of Microsoft Fabric. Create a new pipeline, name it and click create.
- To ingest data to the pipeline, establish connection between the Bing API and Fabric, provide authentication for Fabric to access the 
   data 
- To <u>***Establish the Connection***</u> between the Bing API and Fabric:
   - Copy data activity -> Add to canvas -> name the activity
   - Under the **source tab** of this copy data activity:
       1. For **data store type** , choose **External** 
       2. For the **Connection** , choose **REST**
          - In the **Connection Settings**, give the **Base URL** as https://api.bing.microsoft.com/v7.0/news/search, this is the endpoint               of the Bing API that returns news articles basd on users search query
          - To configure the **Connection Credentials**, click on create new connection, give a name of choice for the connection, and                   choose Anonymous for the Authentication Kind
            ![connection_establishment](/02_Data%20Ingestion/img/di_01.png)
       3. Test if the connection is established or not by clicking the test connection button.
          ![connection_test](/02_Data%20Ingestion/img/di_02.png)
- To <u>***Authenticate the Data Access***</u> between the API and Fabric:
   - Expand the **Advanced section in the source tab** , provide Additional headers : Name ->  Ocp-Apim-Subscription-Key, Value -> Key of 
     the API Endpoint,this can be found under the Keys and Endpoints tab of the API
   - Give the Relative URL : ?q=latest+news&count=100&freshness=Day&mkt=en-IN
     This fetches a response of 100 latest news articles of India, that the Bing API discovered in the past 24 hours.
     ![connection_test](/02_Data%20Ingestion/img/di_03.png)
- To write these responses of the API in the data lakehouse, under the **Destination tab** :
   - Choose Workspace as Data store type
   - Workspace Data Store Type -> Lakehouse
   - Lakehouse -> bing_lake_db (the lakehouse db created as part of environment setup)
   - Root Folder -> Files
   - Give the filename alone under the file path
   - Choose JSON as the file format
     ![connection_test](/02_Data%20Ingestion/img/di_04.png)
- Save the changes and run the pipeline
   ![connection_test](/02_Data%20Ingestion/img/di_06.png)
   ![connection_test](/02_Data%20Ingestion/img/di_07.png)
