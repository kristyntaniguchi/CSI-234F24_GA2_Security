# Renton Technical College CSI-234
<br />    

<div align="center">  
    <img src="logo.jpg" alt="Logo">
    <h3 align="center">Guided Activity 2</h3>
</div>

This repository is a part of CSI-234 at Renton Technical College.

Clone this repository to your local machine and complete the instructions below. You will be submitting screenshots as well as SQL code in this repository

## Guided Activity 2 Part 1 Clone the repository and make a screenshots folder

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

## Part 2: Creating a New Schema and Sample Table

1. Connect to your SQL Database using SQL Server Management Studio or Azure Data Studio.

2. Create a new query window and execute the following SQL to create a new schema and a sample table:

```sql
-- Create a new schema
-- A schema is a logical container for database objects like tables, views, and stored procedures
-- It helps in organizing database objects and can be used for access control
CREATE SCHEMA GA1;
GO

-- Create a sample table in the new schema
-- This table will store employee information
CREATE TABLE GA1.EmployeeData (
    EmployeeID INT PRIMARY KEY,  -- Unique identifier for each employee
    FirstName NVARCHAR(50),      -- First name of the employee
    LastName NVARCHAR(50),       -- Last name of the employee
    Salary DECIMAL(10, 2),       -- Employee's salary (allows for 2 decimal places)
    Department NVARCHAR(50)      -- Department where the employee works
);
GO

-- Insert some sample data into the EmployeeData table
-- This data will be used to test our permissions later
INSERT INTO GA1.EmployeeData (EmployeeID, FirstName, LastName, Salary, Department)
VALUES 
(1, 'John', 'Doe', 50000.00, 'Sales'),
(2, 'Jane', 'Smith', 60000.00, 'HR'),
(3, 'Bob', 'Johnson', 55000.00, 'IT'),
(4, 'Alice', 'Williams', 65000.00, 'Finance');
GO
```

3. Take a screenshot of the query and its results, and save it in the screenshots folder.

## Part 3: Creating Users with Different Levels of Access

In this section, we'll create users with varying levels of access to demonstrate RBAC.

1. Create logins in the master database:

```sql
-- Create logins. Logins are created on the SERVER level in the master database
-- Be sure you run this code ON MASTER
-- A login is a security principal at the server level that allows connection to the SQL Server instance
CREATE LOGIN HRManager WITH PASSWORD = 'HRPass123!';
CREATE LOGIN SalesRep WITH PASSWORD = 'SalesPass123!';
CREATE LOGIN ITSupport WITH PASSWORD = 'ITPass123!';
GO

-- Verify that the logins were created
SELECT *
FROM sys.sql_logins
```

2. Create users in the AdventureWorks database

```sql
-- Create users for the logins
-- A user is a security principal at the database level
-- Switch back to AdventureWorksLT before running this Query
-- Users are mapped to logins and are used to control access to database objects
CREATE USER HRManagerUser FOR LOGIN HRManager;
CREATE USER SalesRepUser FOR LOGIN SalesRep;
CREATE USER ITSupportUser FOR LOGIN ITSupport;
GO

-- Verify that the users were created
SELECT *
FROM sys.database_principals

-- The difference between a login and a user:
-- Login: Server-level principal, used for authentication (connecting to the server)
-- User: Database-level principal, used for authorization (accessing objects within a database)
```

3. Create roles and assign permissions:

```sql
-- Create roles
-- Roles are used to group users and assign permissions collectively
CREATE ROLE HRRole;
CREATE ROLE SalesRole;
CREATE ROLE ITRole;
GO

-- Assign permissions to roles
-- GRANT: Gives a security principal permission to perform an action
-- SCHEMA::GA1 applies the permission to all objects within the GA1 schema

-- SELECT: Allows reading data
-- INSERT: Allows adding new rows
-- UPDATE: Allows modifying existing data
-- DELETE: Allows removing rows
GRANT SELECT, INSERT, UPDATE, DELETE ON SCHEMA::GA1 TO HRRole;

-- SalesRole only needs to view employee data, not modify it
GRANT SELECT ON GA1.EmployeeData TO SalesRole;

-- ITRole needs to view data and update certain information
GRANT SELECT, UPDATE ON GA1.EmployeeData TO ITRole;
GO

-- Assign users to roles
-- This links the users to their respective roles, granting them the role's permissions
ALTER ROLE HRRole ADD MEMBER HRManagerUser;
ALTER ROLE SalesRole ADD MEMBER SalesRepUser;
ALTER ROLE ITRole ADD MEMBER ITSupportUser;
GO
```

4. Add column-level permissions:

```sql
-- Column-level permissions allow for more granular control over data access

-- DENY: Explicitly prevents a security principal from performing an action
-- This ensures that SalesRole cannot view salary information
DENY SELECT ON GA1.EmployeeData(Salary) TO SalesRole;

-- Grant UPDATE permission on specific columns for ITRole
-- This allows IT to update employee information except for salary
GRANT UPDATE ON GA1.EmployeeData(FirstName, LastName, Department) TO ITRole;
DENY UPDATE ON GA1.EmployeeData(Salary) TO ITRole;
GO
```

## Part 4: Testing User Access

Now, we'll test the access for different users to verify the RBAC implementation.

1. Test HRManagerUser access:

```sql
-- EXECUTE AS: This command allows us to switch context to a different user
-- This simulates logging in as the HR Manager
EXECUTE AS USER = 'HRManagerUser';

-- HR should have full access to the employee data
SELECT * FROM GA1.EmployeeData;

-- HR should be able to insert new employee records
INSERT INTO GA1.EmployeeData (EmployeeID, FirstName, LastName, Salary, Department)
VALUES (5, 'Eva', 'Brown', 70000.00, 'Marketing');

-- Check to see the new user is added
SELECT * FROM GA1.EmployeeData;

-- REVERT: This command switches back to our original user context
REVERT;
GO
```

After executing this code, take a screenshot of the results and save it in the screenshots folder.

2. Test SalesRepUser access:

```sql
-- Switch to the Sales Representative user context
EXECUTE AS USER = 'SalesRepUser';

-- Sales should be able to view employee data, but not salary information
SELECT * FROM GA1.EmployeeData;

-- This insert should fail because SalesRole only has SELECT permission
INSERT INTO GA1.EmployeeData (EmployeeID, FirstName, LastName, Salary, Department)
VALUES (6, 'Mike', 'Davis', 52000.00, 'Sales');

REVERT;
GO
```

After executing this code, take a screenshot of the results and save it in the screenshots folder.

3. Test ITSupportUser access:

```sql
-- Switch to the IT Support user context
EXECUTE AS USER = 'ITSupportUser';

-- IT should be able to view all employee data
SELECT * FROM GA1.EmployeeData;

-- This update should succeed (updating department)
UPDATE GA1.EmployeeData SET Department = 'IT Support' WHERE EmployeeID = 3;

-- This update should fail (attempting to update salary)
UPDATE GA1.EmployeeData SET Salary = 58000.00 WHERE EmployeeID = 3;

REVERT;
GO
```

After executing this code, take a screenshot of the results and save it in the screenshots folder.

## Part 5: Explanation of Permissions

In a text file named "PermissionsExplanation.txt", provide brief explanations for the following:

1. Explain the different types of permissions you assigned (SELECT, INSERT, UPDATE, DELETE) and what each allows a user to do.
2. Describe the concept of schema-level permissions vs. table-level permissions.
3. Explain how column-level permissions work and why they might be useful.
4. Discuss the principle of least privilege and how it's applied in this RBAC setup.
5. Explain the potential security benefits of using roles instead of assigning permissions directly to users.

## Submission

1. Ensure all your screenshots are saved in the screenshots folder.
2. Add comments to your SQL code explaining the purpose of each major section.
3. Include the "PermissionsExplanation.txt" file in your repository.
4. Commit your changes with the message "Guided Activity 2 Complete".
5. Push your changes to GitHub.

If you have any questions about this assignment, please reach out to your instructor or the TA for this course.


Feel free to message your instructor or the TA on Canvas if you have any questions.
