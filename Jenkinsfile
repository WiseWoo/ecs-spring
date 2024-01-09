pipeline {
    agent any

    tools {
        maven 'my_maven' 
    }

    environment {
        GITNAME = 'WiseWoo'
        GITMAIL = 'jiwooo0@naver.com'
        GITWEBADD = 'https://github.com/WiseWoo/ecs-spring.git'
        GITSSHADD = 'git@github.com:WiseWoo/ecs-spring.git'
        GITCREDENTIAL = 'git_cre'
        
        DOCKERHUB = 'jiwoo0/ecs_spring'
        DOCKERHUBCREDENTIAL = 'docker_cre'
    }

    stages {
        stage('Checkout Github') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [],
                userRemoteConfigs: [[credentialsId: GITCREDENTIAL, url: GITWEBADD]]])
            }
            post {
                failure {
                    echo 'Repository clone failure'
                }
                success {
                    echo 'Repository clone success'
                }
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('image build'){
            steps{
                // sh "docker build -t WiseWoo/ecs-spring:1.0 ."
                sh "docker build -t ${DOCKERHUB}:${currentBuild.number} ."
                sh "docker build -t ${DOCKERHUB}:latest ."
            }
        }
        stage('image push'){
            steps{
                withDockerRegistry(credentialsId: DOCKERHUBCREDENTIAL, url: '') {
                    sh "docker push ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker push ${DOCKERHUB}:latest"
                }
            }
            
            post {
                failure {
                    echo 'docker image push fail'
                    sh "docker image rm -f ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker image rm -f ${DOCKERHUB}:latest"
                }
                
                success {
                    sh "docker image rm -f ${DOCKERHUB}:${currentBuild.number}"
                    sh "docker image rm -f ${DOCKERHUB}:latest"
                }
            }
        }
    }
}