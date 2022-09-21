
pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy to Staging Environment'){
            steps{
                build job: 'Deploy-Application-Staging-Environment-Pipeline'

            }
            
        }
        stage('Deploy to Production Environment'){
            steps{
                }
                build job: 'Deploy-Application-Production-Environment-Pipeline'
            }
        }
    }
}
