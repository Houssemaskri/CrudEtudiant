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
    }
}
