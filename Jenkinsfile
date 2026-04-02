pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // This actually compiles your code so Sonar can scan it
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
                // Replace this with your actual AWS deployment command
                echo 'Deploying to AWS...' 
            }
        }
    }
}
