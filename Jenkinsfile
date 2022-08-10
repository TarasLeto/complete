pipeline {
    agent any
    stages {
        stage('Build image') {
            when {
                branch 'main'
            steps {
                echo 'Starting to build docker image'

                script {
                    def customImage = docker.build("my-image:${env.BUILD_ID}")
                }
            }
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
                            customImage.push ("${env.BUILD_ID}")
                            customImage.push(" latest" )
                        }
                    }
                }
            }
}
}
}
}
