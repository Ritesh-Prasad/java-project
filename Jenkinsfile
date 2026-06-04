pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('code'){
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
        stage('build image'){
            steps{
                sh 'docker build -t netflix2 .'
            }
        }
        stage('run the container'){
            steps{
                sh 'docker run -d --name cont2 -p 8280:8080 netflix2'
            }
        }
    }
}
