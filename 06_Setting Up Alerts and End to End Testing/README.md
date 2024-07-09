# Setting up Alerts and End to End pipeline testing

- To set up alerts, Data Activator component of Fabric is used.
- Navigate to Data Activator -> Open the news dashboard -> choose positive sentiment % card -> choose more options -> set an alert -> in the
  'Operator' dropdown, choose becomes greater than -> set value to 0 -> choose Teams -> create Alert
   ![01](/06_Setting%20Up%20Alerts%20and%20End%20to%20End%20Testing/img/01.png)
- To test the pipeline, click on the  'Send me a test alert' button in the Data activator
  ![03](/06_Setting%20Up%20Alerts%20and%20End%20to%20End%20Testing/img/03.png)
  ![04](/06_Setting%20Up%20Alerts%20and%20End%20to%20End%20Testing/img/04.png)
- When the pipeline runs everyday at the scheduled time, an alert will be sent on Teams whenever the Positive sentiment % is greater than 0.
