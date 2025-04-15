pipeline {
    agent any

    tools {
        maven 'Maven 3.9.9'  // Make sure Maven is configured in Jenkins
    }

    stages {
        stage('Clone') {
            steps {
                echo "📥 Starting code checkout from Git repository..."
                git 'https://github.com/ashish-panicker/spring-boot-hello-world'
            }
        }

        stage('Build') {
            steps {
                echo "🔨 Building the Spring Boot project with Maven..."
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Docker Build') {
            steps {
                echo "🐳 Building Docker image for the Spring Boot app..."
                sh 'docker build -t springboot-jenkins-demo .'
            }
        }

        stage('Run Container') {
            steps {
                echo "🚀 Running the Docker container on port 8080..."
                sh 'docker run -d -p 8080:8080 springboot-jenkins-demo'
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully! Application should be running on http://localhost:8080"
        }
        failure {
            echo "❌ Pipeline failed. Check logs above for details."
        }
    }
}
