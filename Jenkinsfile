pipeline {
    agent any 

    options {
        timeout(time: 5, unit: 'MINUTES')    // Pipeline will timeout after 5 minutes
        retry(2)                            // Retry the pipeline twice if it fails
        timestamps()                        // Add timestamps to console output
        disableConcurrentBuilds()           // Prevent concurrent builds
    }

    stages {
        stage('Build') {
            steps {
                script {
                    bat 'echo Starting Hello World Pipeline'
                    bat 'javac Hello.java' 
                }
            }
        }

        stage('Execute Script') {
            steps {
                script {
                    bat 'java Hello'
                }
            }
        }
        stage('Archive .class File') {
            steps {
                archiveArtifacts artifacts: '*.class', fingerprint: true
            }
        }
        stage('Clean Workspace') {
            steps {
                cleanWs()
            }
        }
    }
}
