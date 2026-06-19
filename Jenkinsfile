pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Repository checkout completed'
            }
        }

        stage('List Files') {
            steps {
                bat 'dir'
            }
        }

        stage('Print Message') {
            steps {
                echo 'My first Jenkins Pipeline'
            }
        }
    }
}

