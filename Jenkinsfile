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
            
            
            // Define the Maven tool named 'Default Maven'
            def mvn = 'Default Maven'
            
            steps {
            // Execute withSonarQubeEnv to set up SonarQube environment variables
            withSonarQubeEnv("SonarQube") {
                // Run Maven with SonarQube analysis
                sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=spring -Dsonar.projectName='spring'"
            }
            }
        }
    }
}
