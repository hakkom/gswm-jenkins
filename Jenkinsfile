/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'maven:3.9.4-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn clean install'
            }
        }
        /* Pro Umgebung "Entwicklung, Test, Prod" ein Branch. */
        stage('deploy test') {
            when {
                branch 'test'
            }
            steps {
                //sh './deploy.sh OMSTA'
                sh 'echo "This will run.  Allways"'
            }
        }

        stage('deploy master') {
            when {
                branch 'master'
            }
            steps {
                /* Deployment-Skripte mit Namenskonventionen für Konfig-Ordner:
                        cfg_$HOSTNAME/config.xml
                        ...
                   oder:
                        cfg/$HOSTNAME/config.xml
                        ....
                */
                //sh './deploy.sh OMSPNEU'
                sh 'echo "This will run.  Allways"'
            }

            steps {
                /* Deployment-Skripte mit Namenskonventionen für Konfig-Ordner:
                   cfg_$HOSTNAME/config.xml
                   cfg_$HOSTNAME/job.xml
                   cfg_$HOSTNAME/routes/onlineinbox.xml
                   ...
                */
                //sh './deploy.sh OMSPA'
                sh 'echo "This will run. Allways"'
            }
        }
    }
    post {
        always {
            echo 'Ich bin fertig!'
            deleteDir()
            echo 'Verzeichnis gelöscht.'
        }

        failed {
            echo 'Ich hab ein Problem!'
            deleteDir()
            echo 'Verzeichnis gelöscht.'
        }
    }
}
