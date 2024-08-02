# Knight Path Technical Take Home

# Knight Path Technical Take Home

## Overview

This app is implemented using Azure Functions. Azure Functions are use to calculate the shortest path for the knight in chess from the source to target. In this implementation, User calls the first API that triggers the Orchestrator function that gets the source and target values from the API endpoint. This function return the operation ID, stores the source and target values in Azure Table Storage, and also triggers the Calculation function to calculate the shortest path from source to the target. The operation ID is then used to query the shortest path by calling the 2nd API that returns the source, target, operation ID, and the shortest path from the source to target. 

## Requirements

1. **.NET SDK**: Ensure you have .NET 8.0 or higher installed.
2. **VS Code**: Make sure you have Visual Studio 2022 installed.
3. **Azure Development**: Make sure that Azure development checkbox was checked during the installation of Visual Studio 2022.
4. **Azure Development Tools**
   
## Setup and Running the Application

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/your-repo/FinancialApp.git
   cd KnightPathDurableFunctions
To access the functions published on Azure:

•	API 1 Call: Use a tool like Postman to send a POST request to the knightpath endpoint with the source and target positions:

URL: https://knightpathdurablefunctions.azurewebsites.net/api/OrchestratorFunction_HttpStart?source=<source>&target=<target>

Example:
 ![image](https://github.com/user-attachments/assets/2236b897-a56a-44a5-8936-abe54cb210f6)

Here A1 and D5 are start and end positions respectively. The source and target values are provided as A1 and D5 respectively.

It will give the operation ID in response which will then be used in the below API call.

•	API 2 Call: Use a tool like Postman to send a GET request to the knightpath endpoint with the operation ID to retrieve the result:

URL: https://knightpathdurablefunctions.azurewebsites.net/api/QueryKnightPath?operationId=<operationId>

Upon hitting this API, we get the following result:
![image](https://github.com/user-attachments/assets/b824e2f2-59ba-448f-9bb4-65a5d6b161ae)

 
	        The <oprationId> was replaced by the ID returned in the above response.
To run this in a local environment:

•	Open the solution in Visual Studio.

•	Press F5 to run the project.

•	A new console will be opened as shown below:

 ![image](https://github.com/user-attachments/assets/8bb7de2e-8f82-4724-9b5b-460d8fd9ad23)

•	Use a tool like Postman to send a POST request to the knightpath endpoint with the source and target positions:

•	In the above screenshot the URL is: http://localhost:7152/api/OrchestratorFunction_HttpStart?source=<source>&target=<target>

![image](https://github.com/user-attachments/assets/1bbce408-da86-4800-9814-c75e2fcff5df)

 
Here A1 and D5 are start and end positions respectively. The source and target values are provided as A1 and D5 respectively.

•	Use a tool like Postman to send a GET request to the knightpath endpoint with the operation ID to retrieve the result:

•	In the above screenshot the URL is: http://localhost:7152/api/QueryKnightPath?operationId=<operationId>

 ![image](https://github.com/user-attachments/assets/cfe70dbc-dc2e-4239-a6f4-a8185f5abae0)



2. **Restore Dependencies**:

dotnet clean,
dotnet restore

3. **Build the Project**:

dotnet build

4. **Run the Application**:

dotnet run

5. **Run Tests**:

dotnet test
