/* Requires the Docker Pipeline plugin */
pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                timeout(time: 3, unit: 'MINUTES') {
                    retry(5) {
                        sh 'chmod 777  *'
                        sh './flakey-deploy.sh'
                    }
                }
            }
        }
    }
}
