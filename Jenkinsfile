node('Machine') {
    stage('Version Control System') {
        git url: 'https://github.com/krishna6788/game-of-life.git'
            branch: 'Scripted'
        
    }
    stage('Build') {
        sh 'mvn package'
    }
    stage('Artifacts and Junits') {
        archiveArtifacts artifacts: '**/gameoflife.war',
                   allowEmptyArchive: true,
                   fingerprint: true,
                   onlyIfSuccessful: true
        junit testResults: '**/target/surefire-reports/TEST-*.xml'
    }
}