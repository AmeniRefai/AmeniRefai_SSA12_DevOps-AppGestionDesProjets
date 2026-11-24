
pipeline {
    agent any

    stages {

        stage('Recuperation du projet') {
            steps {
                echo 'Recuperation du code source depuis GitHub'
                checkout scm
            }
        }

        stage('Generation du livrable') {
            steps {
                dir('backend') {
                    sh 'chmod +x mvnw'
                    sh './mvnw clean package -DskipTests'
                }
            }
        }

        stage('Archivage du livrable') {
            steps {
                archiveArtifacts artifacts: 'backend/target/*.jar',
                                 fingerprint: true
            }
        }
    }
}
