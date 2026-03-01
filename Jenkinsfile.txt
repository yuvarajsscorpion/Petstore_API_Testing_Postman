pipeline {
    agent any stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/yuvarajsscorpion/Petstore_API_Testing_Postman.git'
            }
        } stage('Run Postman Tests') {
            steps {
                bat 'newman run Petstore_User_Operations_Collection.postman_collection.json -r html'
            }
        }
    } post {
        always {
            archiveArtifacts artifacts: 'newman/*.html', fingerprint: true publishHTML([allowMissing: false, alwaysLinkToLastBuild: true, keepAll: true, reportDir: 'newman', reportFiles: '*.html', reportName: 'Newman Test Report'])
        }
    }
}