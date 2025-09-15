pipeline{
    agent any
    tools {
        jdk 'java-11'
        maven 'maven'
    }
    stages{
        stage('git checkout') {
            steps {
                    git branch: 'main', url: 'https://github.com/praveenkumarchannappagoudra/test-1.git'
            }
        }
        stage('Compile') {
            steps {
                    sh 'mvn compile'
            }         
        }
        stage('Build'){
            steps {
                    sh 'mvn clean install'
            }
        }
        stage('build and tag dockerfile'){
            steps{
                sh 'docker build -t praveenkumarchannappagoudra/project:1 .'
            }
        }
        stage('containersation'){
            steps{
                sh 'docker run -it -d --name c1 -p 8081:8080 praveenkumarchannappagoudra/project:1'
            }
        }

    }
}