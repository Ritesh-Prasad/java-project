pipeline{
    agent any

    tools{
        maven 'maven'
    }

    stages{

        stage('Code'){
            steps{
                git 'https://github.com/Ritesh-Prasad/java-project.git'
            }
        }

        stage('Build'){
            steps{
                sh 'mvn compile'
            }
        }

        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }

        stage('Artifacts'){
            steps{
                sh 'mvn package'
            }
        }

        stage('Build Docker Image'){
            steps{
                sh '''
                docker rmi netflix2 || true
                docker build --no-cache -t netflix2 .
                '''
            }
        }

        stage('Run Container'){
            steps{
                sh '''
                docker stop cont2 || true
                docker rm -f cont2 || true

                docker run -d --name cont2 -p 8280:8080 netflix2
                '''
            }
        }
    }
}
