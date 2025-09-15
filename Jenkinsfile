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
        stage('Docker image scan'){
            steps {
                    sh 'trivy image --format table -o trivy-image-report.html manojkrishnappa/project:1'
            }
        }
        stage('containersation'){
            steps{
                sh '''
                docker stop c1
                docker rm c1
                docker run -it -d --name c1 -p 8081:8080 praveenkumarchannappagoudra/project:1
                '''
            }
        }
        stage('Login to Docker Hub'){
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
                    }
                }
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                sh 'docker push praveenkumarchannappagoudra/project:1'
            }
        }
    }
}