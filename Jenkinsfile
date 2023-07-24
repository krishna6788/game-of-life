pipeline {
    agent { label 'Machine'}
    parameters {
        string(name: 'MAVEN_GOAL',defaultValue: 'package', description: 'maven goal')
    }
    stages {
        stage('Version Control System') {
            steps {
                git url: 'https://github.com/krishna6788/game-of-life.git',
                    branch: 'Declartive'
                    }
                }
        stage('Build Stage') {
            steps {
               tools {
                   jdk 'JDK_8_UBUNTU'
               }

            }
        }
        stage('mvn stage') {
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
            }
        }
        stage('Post Build') {
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
    