pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './mvn clean package --no daemon'
            }
        }
    }
}
      
