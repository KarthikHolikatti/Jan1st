pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
               bat "nant build -Dbuild.Jenkins=True"
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
