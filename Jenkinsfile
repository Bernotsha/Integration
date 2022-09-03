def author
pipeline{
  
  agent any
  
  stages{
   
    stage("build"){
        
      steps{
        echo 'building an application'
        script{
          author = sh(returnStdout: true, script: "git log -1 --pretty=format:'%an'").trim()
          echo "$author"
        }
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
