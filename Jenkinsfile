pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello, Jenkins!'
            }
        }
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
        stage('Docker Build') {
            steps {
                sh 'docker build -t my-mavenapp:latest .'
    }
}
        stage('Deploy') {
            steps {
                sh '''
          	docker stop my-mavenapp || true
        	docker rm my-mavenapp || true
        	docker run -d -p 8081:8080 --name my-mavenapp my-mavenapp:latest
         	'''
    }
}
    }
}

