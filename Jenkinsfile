pipeline {
    agent any
    stages {
        stage("code checkout") {
            steps {
                git "https://github.com/akramshaik12345/spring-petclinic.git"
            }
        }
        stage("build") {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                // Define the Maven tool named 'maven-3.9.5'
                M2_HOME = tool 'maven 3.9.5'
            }
            steps {
                // Execute withSonarQubeEnv to set up SonarQube environment variables
                withSonarQubeEnv("SonarQube") {
                    // Run Maven with SonarQube analysis
                    bat "${M2_HOME}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=spring -Dsonar.projectName='spring'"
                }
            }
        }
    }
}
