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
            steps {
                // Define the Maven tool named 'Maven' within this stage
                def mvn = tool 'Maven'
                
                // Execute withSonarQubeEnv to set up SonarQube environment variables
                withSonarQubeEnv("SonarQube") {
                    // Run Maven with SonarQube analysis using the defined Maven tool
                    bat "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=spring -Dsonar.projectName='spring'"
                }
            }
        }
    }
}
