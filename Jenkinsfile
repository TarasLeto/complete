pipeline {
    agent any
    stages {
        stage ('Build Docker Image') {
            when {
                branch 'main'
            }
            steps {
                script {
                    app= docker.build("gs-rest-service/gs-rest-service")
                    }
                }
    }
            }    
            stage ('Push Docker Image') {
                when {
                    branch 'main'
                }
                steps {
                    script {
                        docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                            app.push ("${env.BUILD_NUMBER}")
                            app.push(" latest" )
                        }
                    }
                }
            }
    }
}
