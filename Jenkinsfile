pipeline {
    agent any
    stages {
        stage ("code checkout") {
            steps {
            git "https://github.com/akramshaik12345/spring-petclinic.git"
            }
        }
        stage ("build") {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
          def mvn = tool 'Default Maven';
            withSonarQubeEnv() {
          sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=spring -Dsonar.projectName='spring'"
            }
         }
                
        
    }
}
