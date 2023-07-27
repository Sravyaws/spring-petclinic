pipeline {
    agent { label 'JDK_17' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/Sravyaws/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
                }
            }
        stage('archiveArtifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.JAR',
                     onlyIfSuccessful: true
                }
            }
        stage('publish test results') {
            steps{
                junit testResults: '**/TEST-*xml',
                  allowEmptyResults: false
               }         
            }
        }       
}        