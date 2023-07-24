pipeline {
    agent { label 'Machine'}
    stages {
        stage('Version Control System') {
            steps {
                git url: 'https://github.com/krishna6788/game-of-life.git'
                    branch: 'Declartive'
                    }
                }
        stage('Build Stage') {
            steps {
                sh 'export PATH="/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH" && mvn package'

            }
        }
        stage('Artifacts and JunittestResults') {
            steps {
                archiveArtifacts artifacts: '**/gameoflife.war',
                   allowEmptyArchive: true,
                   fingerprint: true,
                   onlyIfSuccessful: true
                junit testResults: '**/target/surefire-reports/TEST-*.xml'

            }
        }
            }
        }
    