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
            def mvn = tool 'M2_HOME';
          

                // Execute withSonarQubeEnv to set up SonarQube environment variables
                withSonarQubeEnv("SonarQube") {
                    // Run Maven with SonarQube analysis
                    bat "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=spring -Dsonar.projectName='spring'"
                }
            }
        }
    }

