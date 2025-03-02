pipeline {
    agent any
    tools {
        maven 'maven1'
        jdk 'java17'
    }
    stages {
        stage('Download Code from Git') {
            steps {
                git branch: 'main', url: 'https://github.com/Lakshya110/maven-jenkins6.git'
            }
        }
        stage('Build Java') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Archive the Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
         stage('Build another project') {
            steps {
                build wait: false, job: 'build-deploy-pipeline'
            }
        }
    }
}
