# Renton Technical College CSI-234
<br />    

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Guided Activity 2</h3>
</div>

This repository is a part of CSI-234 at Renton Technical College.

Clone this repository to your local machine and complete the instructions below. You will be submitting screenshots as well as SQL code in this repository

## Guided Activity 2 Part 1 Clone the repository and make a screenshots folder
We will complete this assignment together in class. If you are having problems with this assignment please refer to the lecture recording.

1. Clone the repository to your local machine using GitHub Desktop or other GitHub tool.
2. Make note of the folder where you cloned the repository.
3. Click Show in Explorer to open the repository folder.
4. Inside of this folder create a screenshots folder. This is where you will save your screenshots for this assignmnent.
5. Just to test that it is working take a screenshot of your desktop and save it inside of the screenshots folder.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/f245b2da-4f49-4ee0-a4d6-268367f9e0f8)

6. After saving the screenshot go back to GitHub Desktop. You will notice that changes have taken place.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/b79de131-eaa8-425a-9d26-d0b57a26e5e1)


7. Create a new commit called "Testing Screenshots" and click Push Origin to push the changes to GitHub.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/a98c07f0-b98c-42a3-81a7-1fb3c055d5c5)

8. Go back to your repository in the browser and you will see a new commit with your message.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/03f4e697-f7f8-4e8c-821d-6a18f3fcd8cb)

## Guided Activity Part 2 Creating an Azure SQL Database. Make sure to follow these next steps exactly. If you deploy the database incorrectly you could spend all of your Azure Credits very quickly.

1. Navigate to Azure.com and login with your student email and password that you used to register for Azure for Students last week.
2. In the top search window search for Azure SQL and click on the Azure SQL option.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/ec389fc4-f715-42ad-809b-81849c63bb7e)


3. Click Create on the Azure SQL Page.
4. On the Select SQL Deployment Page, click the drop down under SQL Databases and Choose Database Server and click Create.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/9a16c291-c0e1-4063-839d-56de949ea8c3)


5. On the Create SQL Database Server screen Verify that the subscription says Azure for Students.
6. Under resource group click create new.
7. Choose a name for the group and click Ok.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/ad3ff2cf-7911-4dfd-afc1-fd35c0607884)

8. Choose a name for the server. This name has to be unique among all SQL Servers on Azure so you may have to choose a few different options.
9. In the location drop down select US West 3.


![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/57fabf68-59e8-4aa5-925b-b20d4d7fbf70)

10. Under Authentication Choose Use SQL Authentication.
11. Choose an admin username and password.
12. Make sure to remember this password as you will need it later.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/c14835f8-c1bb-40d5-b03d-3ab06f299237)

13. Click the Networking tab at the top of the page and Click Yes Allow Azure services and resources to access this server.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/1bdc5085-0c9d-436b-8c09-e1e221b0fcd5)

14. Click Review and Create and then Click Create. Your Screen should look something like this when you Create. Your subcription will be different than mine however.
15. Notice the Estimated charges per month. It should say no Additional Charges. Click Create.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/84bbb4c5-12f3-4fe1-9aed-5704b15e51a1)

16. Deployment of your new SQL Server will take some time. You will see ...Deployment in Progress
17. When it is done the screen will display your deployment is complete.
18. Click go to resource when it is complete.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/f9741595-4c71-4f59-9c1f-e6071f321662)



19. You are now looking at the home page for your new SQL Server. It should look something like this.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/e98e326e-f8e1-4184-a22e-e4cbd3aaca43)

20. Now we need to tell Azure to allow connections over the internet.
21. Click on the Networking button on the left side of the Screen.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/7c7edd76-3b80-4742-b935-8272938cbff8)


22. Click on Add your client IPv4 address to allow connections from your current IP to the server.
23. If your IP address changes you will have to create a new rule.
24. Make sure to click Save on this screen.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/3ca0a8f0-a6cb-4dff-ba94-de9d1c6756b2)

25. Take a screenshot of this page after you are done and save it in the screenshots folder.
26. Click Overview in the top left of the screen to return to the Home page for the SQL Server
27. Take a screenshot of the SQL Server home page and save it in the screenshots folder.
28. Create a new commit with Summary "Part 2 Complete" and push the changes to GitHub.

## Guided Activity Part 3 Deploying our sample database
1. At this point is it possible to connect to your SQL Server if you would like to try.
2. The server name is the address you can use along with the port 1433
3. Use SQL Authentication and provide the admin login and password that you made previously.
4. You may use either Azure Data Studio or SQL Server Management Studio

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/2b06fbb0-2f42-4933-9f60-625fa6e07b6e)

5. Once you have connected take a screenshot and add it to the screenshots folder.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/cabb2fef-b11a-4b4a-8195-91303c4e8fbe)

6. Notice that the only database listed is master.
7. master is a database used by SQL Server for login and system information and is not available for general use.
8. In order to deploy our sample data we need to add a database to our server.
9. This is where we will begin to incure charges from Azure SQL. The server is free, the databases are what cost money.
10. Go back to the Server home page in Azure SQL and click Create Database.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/c02760cf-91e9-4c71-b86e-acbf35048f66)

11. Be VERY CAREFUL over these next steps, this is where you can accidentially spend too much money.
12. Choose a database name.
13. Confirm that NO is selected for Usq SQL Elastic Pool.
14. Under Workload environment Click Development

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/b62ee206-44b3-4f86-bc8e-b599c6b43942)


15. Under Compute + Storage click configure database

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/b5f555bd-84dc-42cf-b742-b3ac430879be)

16. Click the drop down next to Seervice Tier and choose Basic (For less demanding workloads) under the DTU-based purchasing model.
17. After you choose this opition you should see to the right that the database will cost $4.90 per month.
18. Click Apply

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/1fdb6e39-b5f7-4857-936d-e8b4371a1a82)

19. You will be taken back to the Create SQL database page.
20. Click Additional Settings at the top.
21. Under Data source: Use Existing Data click on Sample.


![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/4d3bd814-f5e7-4254-992c-a49de7de4ac7)

22. Click Review and Create.
23. Make sure that your estimated charges are still $4.90 per month
24. Click Create.
25. Wait for deployment to complete.
26. Once deployment is complete click Go to resource.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/6a0abe31-f4c8-4f9e-ac5a-7bb91200e338)

27. This is the home page for the Database that you just deployed.
28. Take a screenshot of this page and add it to the screenshots folder.
29. Go back to Azure Data Studio and click refresh on the home page of your server or reconnect to the database

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/b0698892-be86-4214-b7c3-2a2e7d51b8c5)

30. Notice that you now have another database in your server.
31. Click the Connections button in the upper left of Azure Data Studio.
32. Click on the server.
33. Click on Databases.
34. Click on your new sample Database.
35. Click on Tables to view all of the tables in our Sample Database.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/9d3a9f0c-7b6c-4566-a532-a0d6ea9646f3)

36. Take a screenshot of this and add it to the screenshots folder.
37. Right click the SalesLT.Customer table and click select top 1000 rows.

![image](https://github.com/EmeryCSI/CSI234F23_GuidedActivity2/assets/102991550/ecf5b9a7-e6fd-4cc6-b37c-2e099742c638)

38. Take a screenshot of the output and add it to the screenshots folder.
39. Create a new Commit in GitHub Desktop with "Assignment Complete"
40. Push the changes to GitHub.


If you have any questions about this assignment please reach out to myself or our TA for this course. 



Feel free to message your instructor or the TA on Canvas if you have any questions.
