#!/usr/bin/env groovy

pipeline{
    agent any

    stages{
        stage("test"){
            steps {
                echo "Testing the application"
            }
        }

        stage("build"){
            steps {
                echo "Building the application"
            }
        }

        stage("deploy"){
            steps {
                sshagent(['ec2-server-key']) {
                    def dockerCmd = 'docker run -p 3000:80 -d dbynar/demo-app:1:0'
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@18.156.198.140 ${dockerCmd}"
                }
            }
        }
    }
    
}