#!/usr/bin/env groovy

node {

    cleanWs()

    stage('checkout') {
        checkout scm
    }

    stage('check java') {
        sh "java -version"
    }

    stage('build') {
        try {
            sh "./gradlew verify"
        } catch (err) {
            throw err
        } finally {
            junit '**/target/surefire-reports/**/*.xml'
        }
    }
}