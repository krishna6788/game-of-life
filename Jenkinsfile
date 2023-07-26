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
            tools {
                jdk 'JDK_8_UBUNTU'
               }
            
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('Sonar_cloud') { // You can override the credential to be used
                //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
                sh 'mvn clean package sonar:sonar'
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
        
    