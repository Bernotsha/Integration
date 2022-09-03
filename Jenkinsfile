pipeline{
  
  agent any
  
  stages{
   
    stage("build"){
        
      steps{
        echo BRANCH_NAME
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
