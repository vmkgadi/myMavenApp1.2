pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Archive') {
    steps {
        archiveArtifacts artifacts: 'target/*.jar'
    }
}

    }
}

