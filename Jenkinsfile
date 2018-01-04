node{

            stage ("Checkout SCM") {
                     git url:"https://github.com/KarthikHolikatti/Jan1st.git"
                     }
	  
            stage("Build") {
		    	   
                  parallel d: {
                     echo 'intitialize'
                     bat"nant init"
                     }, b:{
                     echo 'Building..propertynames'
                     bat"nant Propertynames"
                     },e:{
			  try {
          currentBuild.result = "SUCCESS"
				  
                     echo 'Building..methods'
                     bat"nant t"
				  
	     }//try    
			  catch (Exception err) {
                    currentBuild.result = "FAILURE"
		    bat"nant build"
                    def errorMessage = "defining message"
				  emailext (
      subject: "STARTED:",
      body: "body",
      recipientProviders:  [[$class: 'DevelopersRecipientProvider']]
    )
                    throw err
            }//catch
            finally {
                    def finalMessage ="defining final message"
                    echo finalMessage
	    }      
		     },g:{
                     echo 'Building..methods'
                     bat"nant methodTest10"
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
/*
pipeline{
	agent any 
	stages{
	stage("init"){ 
		steps{
			echo 'hi from init'
			bat"nant init"
		}
	}
	}
}
*/
