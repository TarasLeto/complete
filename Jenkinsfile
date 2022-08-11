pipeline {
    environment { 
        registry = "tarasleto96/gs_rest-service" 
        registryCredential = 'docker_hub_login' 
        dockerImage = '' 
    }
    agent any
    stages {
        stage ('Build Docker Image') {
            when {
                branch 'main'
            }
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                    }
                }
    }
             
            stage ('Push Docker Image') {
                when {
                    branch 'main'
                }
                steps {
                    script {
                        docker.withRegistry('', registryCredential) {
                            dockerImage.push("lts")
                        }
                    }
                }
            }
    }
}

