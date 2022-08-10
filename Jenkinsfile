pipeline {
    agent any
stage ('Build Docker Image') {
            when {
                branch ''
            }
            steps {
                script {
                    app= docker.build("tarasleto96/repo-images-test")
                    app.inside {
                         sh 'echo $(curl localhost:8080)'      
                    }
                }
    }
            }    
            stage ('Push Docker Image') {
                when {
                    branch ''
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
