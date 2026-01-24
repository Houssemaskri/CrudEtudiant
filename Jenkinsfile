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
                sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.33.10:9000/ -Dsonar.token=squ_4020a552c7286b5a74187b499d43770bd14c9a2e'
            }
        }
    }
}
