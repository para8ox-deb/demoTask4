pipeline {
    agent {
        label 'docker-node' // Use the label for your Docker agent
    }

    options {
        timeout(time: 5, unit: 'MINUTES')
        retry(2)
        timestamps()
        disableConcurrentBuilds()
    }

    environment {
        GIT_REPO = 'https://github.com/para8ox-deb/demoTask4.git'
        BRANCH = 'main'  // Specify the branch to checkout
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    echo 'Cloning the repository...'
                    git branch: env.BRANCH, url: env.GIT_REPO
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the Java application...'
                    bat 'javac Hello.java'
                }
            }
        }

        stage('Execute Script') {
            steps {
                script {
                    echo 'Executing the Hello Java program...'
                    bat 'java Hello'
                }
            }
        }
    }
}
