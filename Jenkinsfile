pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/dremxyz/detection-rules.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building project..."'
            }
        }
    }
}