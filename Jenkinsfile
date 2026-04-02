pipeline {
    agent any
    
    // Add this block so Jenkins knows where 'mvn' is
    tools {
        maven 'maven3' 
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('My Sonar Server') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to AWS...'
            }
        }
    }
}
