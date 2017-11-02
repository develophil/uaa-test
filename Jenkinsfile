#!/usr/bin/env groovy

node {
    stage('checkout') {
        checkout scm
    }

    stage('check java') {
        sh "java -version"
    }

    stage('clean') {
        sh "chmod +x gradlew"
        sh "./gradlew clean --no-daemon"
    }
    
    stage('quality analysis') {
        withSonarQubeEnv('Sonar') {
            sh "./gradlew sonarqube --no-daemon"
        }
    }
    
}
