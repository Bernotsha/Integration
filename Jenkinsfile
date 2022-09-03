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
                  
                  def publisher = LastChanges.getLastChangesPublisher "PREVIOUS_REVISION", "SIDE", "LINE", true, true, "", "", "", "", ""
                  publisher.publishLastChanges()
                  def htmlDiff = publisher.getHtmlDiff()
//                   mail bcc: '', body: "${htmlDiff}", cc: '', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: 'Code check in done', to: 'funtimeprojectsofus@gmail.com'

                  writeFile file: 'build-diff.html', text: htmlDiff
                    emailext (
                      subject: "Jenkins - changes of ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                      attachmentsPattern: '**/*build-diff.html',
                      mimeType: 'text/html',
                      body: """<p>See attached diff of build <b>${env.JOB_NAME} #${env.BUILD_NUMBER}</b>.</p>
                        <p>Check build changes on Jenkins <b><a href="${env.BUILD_URL}/last-changes">here</a></b>.</p>""",
                      to: "funtimeprojectsofus@gmail.com" )
                  
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
