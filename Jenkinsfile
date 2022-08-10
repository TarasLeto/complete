pipeline {
        agent {
            any {
                args '--privileged -v $HOME/.m2:/home/jenkins/.m2 -ti -u 496 -e MAVEN_CONFIG=/home/jenkins/.m2 -e MAVEN_OPTS=-Xmx2048m'
            }
        }
        stages {
            stage('Build') {
                steps {
                    script {
                        maven.cleanPackage()
                    }
                }
            }
        }
    }
      
