pipeline {
    agent any

    stages {
        stage('GITClone') {
            steps {
                git 'https://github.com/animishd/simplejavacode_maven.git'
            }
        }
         stage('MAVENTest') {
            steps {
                sh 'mvn test'
            }
        }
         stage('MAVENPackage') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Execute') { 
        // To do this Step we need to update the Linux Sudoers (vi /etc/sudoers) with Jenkins user 
            steps {
                sh 'java -jar target/*.jar'
            }
        }
        stage('JUNITTest') { 
        // To do this Step we need to update the Linux Sudoers (vi /etc/sudoers) with Jenkins user 
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
        stage('Artifact') { 
        // To do this Step we need to update the Linux Sudoers (vi /etc/sudoers) with Jenkins user 
            steps {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}
