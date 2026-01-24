pipeline {
    agent any
    stages {
        stage('checkout GIT') {
            steps {
                echo 'pulling...'
                git branch: 'master',
                    url: 'https://github.com/Houssemaskri/CrudEtudiant'
            }
        }

        stage('Clean') {
            steps {
                sh 'mvn clean verify'
            }
        }
        
        stage('build') {
            steps {
                sh 'mvn compile'
            }
        }
        
        stage('MVN SONARQUBE') {
            steps {
                withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
                    sh """
                      mvn sonar:sonar \
                      -Dsonar.host.url=http://192.168.33.10:9000/ \
                      -Dsonar.token=$SONAR_TOKEN \
                      -Dsonar.junit.reportPaths=target/surefire-reports \
                      -Dsonar.coverage.jacoco.xmlReportPaths=target/site/jacoco/jacoco.xml
                    """
                }
            }
        }
    }
}
