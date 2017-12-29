pipeline {
    agent any
    stages {
        stage ("Checkout SCM") {
            steps{
            git url:"https://github.com/Rajeshkrishnamurthy5/dotnet.git"
            }
        }
        stage("Build") {
            steps {
           parallel d: {
                echo 'intitialize'
               bat "nant init"
            }, a: {
                echo 'Building.. build'
               bat "nant build"
            }, b:{
                echo 'Building..propertynames'
               bat "nant Propertynames"
            },c:{
                echo 'Building..methods'
               bat "nant methodTest1"
            }
                 }
        }
        stage("Test") {
            steps {
                echo 'Testing..'
            } 
        }
        stage("Deploy") {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
