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
            // Define the Maven tool named 'Maven' at the stage level
            tools {
                maven 'Maven'
            }
            steps {
                // Execute withSonarQubeEnv to set up SonarQube environment variables
                withSonarQubeEnv("SonarQube") {
                    // Run Maven with SonarQube analysis using the defined Maven tool
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=spring -Dsonar.projectName='spring'"
                }
            }
        }
    }
}
