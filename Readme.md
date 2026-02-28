# Petstore User Operations Postman Collection
This repository contains a Postman collection for the **Petstore User Operations API**. Use it to explore the API endpoints, run tests, and automate workflows.

## Prerequisites
**[Postman Desktop App](https://www.getpostman.com):** Ensure you have the Postman desktop application installed. 
A valid Git setup if you want to manage this collection with version control. 

## Getting Started 
Follow these steps to get the collection running in your Postman workspace: 

### 1. Download Files
Download the following files from this repository: * `Petstore_User_Operations_Collection.postman_collection.json` (the main collection file) 

### 2. Import into Postman 
Open the [Postman app](https://www.getpostman.com). 
Click the **Import** button in the top left corner. 
Select the `.json` file you downloaded in Step 1 and click **Open**. 

### 3. Configure Environment Variables
The collection uses environment variables to manage dynamic values: 

`petstoreBaseUrl` → Base URL for the Petstore API (default: `https://petstore.swagger.io`) 
`user1_id`, `user2_id`, `user1_username`, `user2_username` → Populated automatically by the **Create List of Users** request 
`update_id` → Populated automatically by the **Update User** request

Ensure you select the correct environment in Postman (e.g., **AI DEMO**) before running the collection. 

### 4. Send Requests 
Select the **Collections** tab in the left sidebar and expand **Petstore User Operations Collection**. 
Navigate through the requests: 
	* `Create List of Users` 
	* `Get User by Username` 
	* `Update User` 
	*'Delete User by Username'
Click the **Send** button in the request pane to execute the request. 
The response will appear in the response pane below. 

## Usage and Testing
1. **Organized Endpoints:** Requests are arranged by API operations.
2. **Automated Testing:** Each request includes pre-built tests (see the "Tests" tab) to validate API behavior, response codes, headers, and data integrity.
3. **Collection Runner:** You can run the entire collection in sequence using the **Collection Runner** to perform end-to-end test flows. 

## Git Workflow: Remote & Local Repository Setup 
To manage this collection with Git and GitHub: 

1. **Create Remote Repository (GitHub)** 
	[Petstore_API_Testing_Postman](https://github.com/yuvarajsscorpion/Petstore_API_Testing_Postman.git) 
2. **Initialize Local Repository (Git)**
	git init
3. **Connect Local to Remote Repository:**
	git remote add origin https://github.com/yuvarajsscorpion/Petstore_API_Testing_Postman.git
4. **Add files to Index/Staging:**
	git add Petstore_User_Operations_Collection.postman_collection.json
5. **Commit Changes:**
	git commit -m "First Commit"
6. **Push to Remote Repository:**
	git push origin master
	
## 📊 Generating Reports
You can generate reports from the Postman collection runs using **Newman** (Postman’s CLI tool) or integrate them into CI/CD pipelines like Jenkins.

### CLI Report
Run the collection directly from the command line: 
newman run "Petstore_User_Operations_Collection.postman_collection.json"

### Newman HTML Report
newman run "Petstore_User_Operations_Collection.postman_collection.json" -r html

## ⚙️ Jenkins Integration
To automate report generation in Jenkins:
1. In your Jenkins job configuration, go to Build → Build Command.
2. Add the following command:
newman run "Petstore_User_Operations_Collection.postman_collection.json" -r html
3. Click Build Now to execute the collection and generate the HTML report.
4. Reports will be available in the Jenkins workspace.

## ✅ Summary
Use Newman CLI for quick command-line runs.
Use Newman HTML Reporter for detailed, shareable reports.
Integrate with Jenkins for automated test execution and reporting in CI/CD pipelines.
