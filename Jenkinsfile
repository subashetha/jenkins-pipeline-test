pipeline {
    agent any
    
    tools {
        maven 'maven3' 
    }

    stages {
        stage('Build') {
            steps {
                // ADD '-f jenkins-pipeline-test/pom.xml' HERE
                sh 'mvn -f jenkins-pipeline-test/pom.xml clean package -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('My Sonar Server') {
                    // ADD '-f jenkins-pipeline-test/pom.xml' HERE TOO
                    sh 'mvn -f jenkins-pipeline-test/pom.xml sonar:sonar'
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
