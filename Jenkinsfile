pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6'  // Ensure this is set in Jenkins Global Tools config
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/your-username/springboot-jenkins-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t springboot-jenkins-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:8080 springboot-jenkins-demo'
            }
        }
    }
}
