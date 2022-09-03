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
        script {
                  
                     def publisher = LastChanges.getLastChangesPublisher null, "SIDE", "LINE", true, true, "", "", "", "", ""
                    publisher.publishLastChanges()
                    def diff = publisher.getDiff()
                    writeFile file: 'build.diff', text: diff
                    emailext (
                      subject: "Jenkins - changes of ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                      attachmentsPattern: '**/*.diff',
                      mimeType: 'text/html',
                      body: """<p>See attached diff of <b>${env.JOB_NAME} #${env.BUILD_NUMBER}</b>.</p>
                        <p>Check build changes on Jenkins <b><a href="${env.BUILD_URL}/last-changes">here</a></b>.</p>""",
                      to: "funtimeprojectsofus@gmail.com")
                  
                } 
      }
    }
    stage("checkout"){
      steps{
        echo 'checking out an application'
      }
    }    
  }

}
