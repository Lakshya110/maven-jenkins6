pipeline {
    agent any
    tools{
        maven 'maven1'
        jdk 'java17'
    }
    stages {
        stage('Download Code from Git') {
            steps {
                git branch: 'main', url: 'https://github.com/Lakshya110/maven-jenkins6/'                                                              
            }
        }
        stage('Build Java Project') {
            steps {
                sh 'mvn clean package '
            }
        }
        stage('Archive the artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('Build a job') {
            steps {
                build wait: false, job: 'deploy-dev-pipeline2'
            }
        }
    }
}
