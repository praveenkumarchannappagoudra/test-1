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

    }
}