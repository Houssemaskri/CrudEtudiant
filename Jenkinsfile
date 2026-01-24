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
                      -Dsonar.token=$SONAR_TOKEN
                    """

                
            }
        }
    }
}
