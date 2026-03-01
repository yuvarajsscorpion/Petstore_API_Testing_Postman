# How to Run in Jenkins
This project uses a Jenkins pipeline defined in the `Jenkinsfile` to run Postman tests with Newman and publish HTML reports. 

## Steps to Run 
1. **Ensure Jenkins is Installed** 
	- Install Jenkins on your machine or server. 
	- Make sure the following plugins are installed: 
		- Git Plugin 
		- Pipeline Plugin 
		- HTML Publisher Plugin 

2. **Configure Jenkins Job** 
	- Create a new **Pipeline Job** in Jenkins. 
	- Under **Pipeline Definition**, select **Pipeline script from SCM**. 
	- Choose **Git** as SCM and provide the repository URL: 
		https://github.com/yuvarajsscorpion/Petstore_API_Testing_Postman.git
	- Set branch to `master`. 

3. **Pipeline Script** 
	Jenkins will automatically detect the `Jenkinsfile` in the repo root. The pipeline performs the following: 
		groovy pipeline { 
						agent any 
						
						stages {
							stage('Checkout') { 
								steps { 
									git branch: 'master', 
										url: 'https://github.com/yuvarajsscorpion/Petstore_API_Testing_Postman.git' 
										} 
									} 
									
							stage('Run Postman Tests') {
								steps { 
									bat 'newman run Petstore_User_Operations_Collection.postman_collection.json -r html' 
									} 
								} 
							} 
							
							post { 
								always { 
									archiveArtifacts artifacts: 'newman/*.html', fingerprint: true 
									publishHTML([ 
										allowMissing: false, 
										alwaysLinkToLastBuild: true, 
										keepAll: true, 
										reportDir: 'newman', 
										reportFiles: '*.html', 
										reportName: 'Newman Test Report' 
										]) 
									} 
								} 
							}
							
4. **Run the Job** 
	- Click Build Now in Jenkins.
	- Jenkins will:
		- Checkout the GitHub repo.
		- Run Newman tests.
		- Archive the HTML report.
		- Publish the report in Jenkins UI.
		
5. **View Reports** 
	- After the build, go to the job’s Build History.
	- Open the latest build → HTML Report link.
	- Review the Newman test results directly in Jenkins.