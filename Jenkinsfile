pipeline {
    agent('lable JDK_17')
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/Sravyaws/spring-petclinic.git',
                    branch: 'declarative'
            }
            stages('build') {
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
                junit testResults: '**/TEST-*xml',
                      allowEmptyResults: false
            }
        }
    }
}