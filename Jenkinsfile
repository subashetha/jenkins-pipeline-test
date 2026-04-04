pipeline {
    agent any
    
    tools {
        maven 'maven3' 
    }

    stages {
        stage('Build') {
            steps {
                // Just 'pom.xml', no folder prefix needed
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('My Sonar Server') {
                    // Just 'pom.xml' here too
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
