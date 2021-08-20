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
                    sh "scp docker-compose.yml ec2-user@18.156.198.140:/home/ec2-user"
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@18.156.198.140 docker-compose -f docker-compose.yml up -d"
                }
            }
        }
    }
    
}