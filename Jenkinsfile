pipeline {
    agent any

    tools {
        maven 'my_maven' 
    }

    environment {
        GITNAME='WiseWoo'
        GITMAIL='jiwooo0@naver.com'
        GITWEB='https://github.com/WiseWoo/ecs-spring.git'
        GITSSHADD='git@github.com:WiseWoo/ecs-spring.git'
        GITCREDENTIAL='git_cre'
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
    }
}