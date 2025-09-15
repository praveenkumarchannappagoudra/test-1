pipeline{
    agent any

    tools {
        jdk 'JDK11'
        maven 'Maven'
    }

    stages{
        stage('Git checkout') {
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