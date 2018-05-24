pipeline {
    agent any
    
    tools {
        maven 'mylocalMaven'
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'Deploy-to-staging'
            }
        }

        stage ('Deploy to Production'){
            steps {
               sh "cp -R **/target/*.war /tmp"
               sh "cp -r webapp.war /tmp//Users/bindhuchinnadurai/Documents/TomcatDocker/tomcatvolume/tomcat/data/"
                 }
            }
        }
}
