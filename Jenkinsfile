#!/usr/bin/env groovy

node {

    cleanWs()

    agent {
        docker { image 'amazoncorretto:17-al2023-jdk' }
    }

     stage('Install git') {
        sh 'yum install git -y'
     }

    stage('checkout') {
        checkout scm
    }

    stage('check java') {
        sh "java -version"
    }

    stage('build') {
        try {
            sh "./gradlew test"
        } catch (err) {
            throw err
        } finally {
            junit '**/target/surefire-reports/**/*.xml'
        }
    }
}