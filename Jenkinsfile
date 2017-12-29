pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
               bat "nant build"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            } 
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
