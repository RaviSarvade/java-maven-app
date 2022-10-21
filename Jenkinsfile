#!/usr/bin/env groovy
def gv
pipeline {
    agent any
    tools {
        maven 'Maven-3.8.6'
    }
    stages {
        stage ("building") {
            steps {
                script {
                    echo "its in building stage."
                    sh "mvn package"
                }
            }            
        }
        stage ("building docker image") {
            steps {
                script {
                    WithCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'PASS', usernameVariable: 'USER' )]) {
                        sh "docker build -t nobleaces9/my-repo:v6 ."
                        sh "echo $PASS | docker login -u $USER --password-stdin"
                        sh "docker push nobleaces9/my-repo:v6"        
                    }
                }
            }
        }

                
           
           
    }
}
