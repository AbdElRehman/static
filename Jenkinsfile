pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Upload to AWS') {
             steps {
                 withAWS(credentials:'aws-static') {
                 sh 'echo "Uploading content with AWS creds"'
                 s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-jenkins-pipeline-123443214324')
                  }
              }
         }
     }
}
