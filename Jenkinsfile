#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        maven 'Maven-3.8.6'
    }
    stages {
        stage ("building") {
            steps {
                echo "its in building stage"
                sh "mvn package"
            }            
        }
        stage ("building docker image") {
            steps {
                echo "its in testing stage"
                WithCredentials ([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'PASS', usernameVariable: 'USER' )]) {
                    sh "docker build -t nobleaces9/my-repo:v6 ."
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                    sh "docker push nobleaces9/my-repo:v6"                  
                }
            }
        }
        stage ("tesing") {
            steps {
                echo "its in testing stage"
                
            }
        }     
    }
}
