Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any
		
    tools {
        maven 'my_maven' 
    }

    environment {
      GITNAME='WiseWoo'
      GITMAIL='jiwooo0@naver.com'
      GITWEB='https://github.com/WiseWoo/ecs-spring.git'
      GITSSHADD='git@github.com:WiseWoo/ecs-spring.git
      GITCREDENTIAL='git_cre'
    }
		
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
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
