pipeline{
  
  agent any
  
  stages{
   
    stage("build"){
        
      steps{
        echo GIT_COMMITTER_EMAIL
        echo 'building an application'
      }
    }
    stage("deploy"){
        
      steps{
        echo 'deploying an application'
      }
    }
    stage("checkout"){
        
      steps{
        echo 'checking out an application'
      }
    }    
  }

}
