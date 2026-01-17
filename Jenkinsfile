pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Récupération du code source') {
            steps {
                echo 'Clonage du dépôt Git...'
                checkout scm
            }
        }

        stage('Affichage de la date système') {
            steps {
                echo 'Date système :'
                sh 'date'
            }
        }
    }
}

