pipeline {
    agent any
    stages {
        stage ('Build Docker Image') {
            when {
                branch 'main'
            }
            steps {
                script {
                    dockerImage = docker.build("tarasleto96/repo-images-test")+ "$BUILD_NUMBER"
                    }
                }
    }
             
            stage ('Push Docker Image') {
                when {
                    branch 'main'
                }
                steps {
                    script {
                        docker.withRegistry('', docker_hub_login) {
                            DockerImage.push ("${env.BUILD_NUMBER}")
                            DockerImage.push(" latest" )
                        }
                    }
                }
            }
    }
}

