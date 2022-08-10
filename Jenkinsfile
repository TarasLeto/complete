pipeline {
    agent any
    stages {
        stage ('Build Docker Image') {
            when {
                branch 'main'
            }
            steps {
                script {
                    app= docker.build("tarasleto96/repo-images-test")
                    }
                }
    }
             
            stage ('Push Docker Image') {
                when {
                    branch 'main'
                }
                steps {
                    script {
                        docker.withRegistry('docker_hub_login') {
                            app.push ("${env.BUILD_NUMBER}")
                            app.push(" latest" )
                        }
                    }
                }
            }
    }
}

