pipeline {
    agent any
    try {
          currentBuild.result = "SUCCESS"
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
            },e:{
                echo 'Building..methods'
               bat "nant methodTest9"
            },g:{
                echo 'Building..methods'
               bat "nant methodTest10"
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
        
                  catch (err) {
                    currentBuild.result = "FAIURE"

                    //hipchat message that the build has failed
                    def errorMessage = "defining message"
                    //hipchatSend color: 'RED', message: errorMessage

                    //send an email that the build has failed
                    mail body: "Project build error: ${err}" ,
                      from: 'Rajesh.Krishnamurthy@oneadvanced.com',
                      replyTo: 'Rajesh.Krishnamurthy@oneadvanced.com',
                      subject: "failed",
                      to: 'Rajesh.Krishnamurthy@oneadvanced.com'

                    throw err
            }
            finally {
                    def finalMessage ="defining final message"
                    echo finalMessage
            }    
    }
}
