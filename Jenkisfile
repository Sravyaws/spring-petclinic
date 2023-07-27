node('JDK_17') {
    stage('VCS') {
        git url: https://github.com/Sravyaws/spring-petclinic.git,
            branch: scripted
    }
    stage('Buils') {
        sh 'mvn clean package'
    }
    stage('archive the artifacts') {
        archiveArtifacts artifacts: '**/target/*.WAR',
                         onlyIfSuccessful: true
    }
    stage('Publish test results') {
        junit testResults: '**/TEST-*xml',
              allowEmptyResults: false
    }
}