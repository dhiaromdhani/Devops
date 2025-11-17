 pipeline {
    agent any

    // Définition des paramètres
    environment {
        GIT_REPO = 'https://github.com/dhiaromdhani/Devops.git'
        BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis GitHub
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                // Nettoyer et compiler le projet Maven
                sh 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                // Archiver le livrable (dans target)
                archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminée avec succès !'
        }
        failure {
            echo 'La pipeline a échoué.'
        }
    }
}

