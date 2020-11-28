pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                dir("/home/julio/repos/ejemplo-maven") {
                    sh "./mvnw clean compile -e"
                }
            }
        }
        
        stage('Test') {
            steps {
                dir("/home/julio/repos/ejemplo-maven") {
                    sh "./mvnw clean test -e"
                }
            }
        }
        
        stage('Package') {
            steps {
                dir("/home/julio/repos/ejemplo-maven") {
                    sh "./mvnw clean package -e"
                }
            }
        }
        
        stage('Run background') {
            steps {
                dir("/home/julio/repos/ejemplo-maven") {
                    sh "nohup bash mvnw spring-boot:run &"
                    sh 'sleep 10'
                }
            }
        }
        
        stage('Testing') {
            steps {
                sh "curl -X GET 'http://localhost:8081/rest/mscovid/test?msg=testing'"
            }
        }
    }
}
