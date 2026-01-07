pipeline {
    agent none

    stages {

        stage('Build') {
            agent { label 'Agent1' }
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build & Push Docker Image') {
            agent { label 'Agent1' }
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'DockerHub',
                    usernameVariable: 'DockerHubUsername',
                    passwordVariable: 'DockerHubPassword'
                )]) {
                    sh '''
                        docker login -u $DockerHubUsername -p $DockerHubPassword
                        docker build -t eureka-server:latest .
                        docker tag eureka-server:latest $DockerHubUsername/eureka-server:latest
                        docker push $DockerHubUsername/eureka-server:latest
                    '''
                }
            }
        }

        stage('Deploy to Production') {
            agent { label 'Agent1' }
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'DockerHub',
                    usernameVariable: 'DockerHubUsername',
                    passwordVariable: 'DockerHubPassword'
                )]) {
                    sh '''
                        docker login -u $DockerHubUsername -p $DockerHubPassword
                        docker compose pull
                        docker compose down || true
                        docker compose up -d
                    '''
                }
            }
        }
    }
}
