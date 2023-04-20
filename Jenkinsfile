pipeline {
agent any
 
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
     stage('deploy') { 
            steps {
               sh 'mvn verify' 
            }
     }
   stage('SonarQube Analysis') {
    steps{
     sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=Vansh_webapp'
    }
  }
 }
}
