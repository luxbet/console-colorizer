#!/usr/bin/env groovy

// For some good examples of how to use the Jenkinsfile syntax, see
// http://www.paasmag.com/2016/06/27/top-10-best-practices-for-jenkins-pipeline-plugin/

node('java18') {
    wrap([$class: 'AnsiColorBuildWrapper', 'colorMapName': 'XTerm', 'defaultFg': 1, 'defaultBg': 2]) {

        try {
            stage('Unit Tests') {
                checkout scm
                sh 'mvn clean test'
            }

            stage('Publish') {
                sh 'mvn deploy'
            }

        } catch (e) {
            println "THE BUILD FAILED"
            throw e
        }

    }
}
