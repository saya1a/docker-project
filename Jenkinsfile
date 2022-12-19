pipeline {
    agent {label "docker-agent"}
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-satish')
    }
    stages{
        stage("clone code from git repo"){
            steps{
                git "https://github.com/saya1a/docker-project.git"
            }
            
        }
        stage('build docker image'){
            steps{
                sh 'docker build -t satishalla/nodeapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub'){
            steps{
                sh 'docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
            }
        }
        stage('push image to docker hub'){
            steps{
                sh 'docker push satishalla/nodeapp:$BUILD_NUMBER'
            }
        }
    }
}
