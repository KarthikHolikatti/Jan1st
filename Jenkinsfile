node{
	pipeline{
		agent any
            stage ("Checkout SCM") {
                     git url:"https://github.com/Rajeshkrishnamurthy5/dotnet.git"
                     }
	  
            stage("Build") {
		    	   
                  parallel d: {
                     echo 'intitialize'
                     bat "nant init"
                     }, b:{
                     echo 'Building..propertynames'
                     bat "nant Propertynames"
                     },e:{
			  try {
          currentBuild.result = "SUCCESS"
				  
                     echo 'Building..methods'
                     bat "nant init"
				  
	     }//try    
			  catch (Exception err) {
                    currentBuild.result = "FAILURE"
			                     bat "nant build"
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
            }//catch
            finally {
                    def finalMessage ="defining final message"
                    echo finalMessage
	    }      
		     },g:{
                     echo 'Building..methods'
                     bat "nant methodTest10"
                     } 
	    }
                    
   //stage-build
				  
      stage("Test") {
               
                  echo 'Testing..'
                 
              }//stage-test
			  
           stage("Deploy") {
                
                 echo 'Deploying....'
                 
              }//stage-deploy
	}  
}
