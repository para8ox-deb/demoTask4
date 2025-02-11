pipeline {
    agent {
        label 'docker-node' // Use the label for your Docker agent
    }

    options {
        timeout(time: 5, unit: 'MINUTES')
        retry(2) // Retry the *entire pipeline* - not ideal for compilation errors
        timestamps()
        disableConcurrentBuilds()
    }

    stages {
        stage('Build') {
            steps {
                script {
                    bat 'echo Starting Hello World Pipeline'
                    bat 'javac Hello.java'
                    // Check for compilation errors
                    if (bat.execute() != 0) {
                        error("Compilation failed!") // Or throw an exception to stop the pipeline
                    }
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
    }
}
