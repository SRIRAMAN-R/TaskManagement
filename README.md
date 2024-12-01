#Task Management API
This is a simple API for managing tasks. It allows users to create, read, update, and delete tasks. Additionally, users can filter tasks based on status and due date, and export tasks to a CSV file.


Prerequisites
Before running the project, ensure that you have the following installed:

.NET SDK 9.0 or higher
Visual Studio or Visual Studio Code
Postman or any other API testing tool (Optional for testing the APIs)
Steps to Run the Project Locally
Clone the repository:

git clone https://github.com/yourusername/TaskManagementApi.git
Navigate to the project directory:

cd TaskManagementApi
Restore the NuGet packages:

Use the following command to restore all dependencies:

dotnet restore
Build the project:

After restoring the dependencies, build the project using the following command:

dotnet build
Run the project:

To run the project locally, use the following command:

dotnet run
This will start the application, and you should see a message like Now listening on: https://localhost:5001.

API Endpoints
1. Get All Tasks
URL: /api/tasks
Method: GET
Query Parameters:
status: (Optional) Filter by task status (NotStarted, InProgress, Completed).
dueDate: (Optional) Filter by tasks that are due before the specified date.
pageNumber: (Optional) The page number for pagination (default is 1).
pageSize: (Optional) The number of tasks to return per page (default is 10).
Response: A list of tasks matching the query parameters.
2. Get Task by ID
URL: /api/tasks/{id}
Method: GET
Response: A single task with the specified ID.
3. Create a New Task
URL: /api/tasks
Method: POST
Request Body:
{
  "title": "Task Title",
  "status": "NotStarted",
  "description": "Task description",
  "dueDate": "2024-12-01T00:00:00Z"
}
Response: The created task with its ID.
4. Update an Existing Task
URL: /api/tasks/{id}
Method: PUT
Request Body: Same format as "Create a New Task."
Response: No content (status code 204) if successful.
5. Delete a Task
URL: /api/tasks/{id}
Method: DELETE
Response: No content (status code 204) if successful.
6. Export Tasks to CSV
URL: /api/tasks/export
Method: GET
Response: A CSV file containing all tasks.
Swagger UI
Swagger UI has been implemented for easy testing and documentation of the API.

URL: /swagger
Once the application is running, you can navigate to https://localhost:5001/swagger (or the relevant URL if you're using a different port) to interact with the API using Swagger UI.
Bonus Features
1. CSV Export
This feature allows you to export all tasks to a CSV file via the /api/tasks/export endpoint. This is particularly useful for generating reports or for data processing tasks.

2. In-Memory Database for Development
The API uses an in-memory database for quick testing and development. For production, you can switch to an actual database (e.g., SQL Server, PostgreSQL) by modifying the TaskDbContext configuration in Program.cs.

Running Tests
1. Unit Tests
The project includes unit tests using NUnit and Moq to mock services.
Tests are located in the TaskManagementApi.Tests project.
To run the tests, use the following command:

dotnet test
2. Integration Tests
The integration tests are designed to test the API endpoints.
The tests use an in-memory database to validate the logic of the application.
To run the integration tests, use:

dotnet test
