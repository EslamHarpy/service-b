pipeline{
    agent any 
    tools {
        maven 'maven-3.9.15'
        jdk 'jdk-17'
    }
    stages{
        stage('first stage '){
            steps{
                sh 'date'
                sh 'echo hello from iti'
                sh 'whoami'
                sh 'pwd'
            }
        
        }
        stage('clone'){
            steps{
                git branch : 'main',
                url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }
        stage('change config'){
            steps{
                sh 'echo server.port=8081 >> src/main/resources/application.properties'
            }
        }
        stage('compile'){
            steps{
                sh 'mvn clean compile'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run'){
            steps{
                sh 'nohup java -jar target/*.jar --server.port=8081 > app.log 2>&1 & sleep 300'
            }
        }
    }   
}
