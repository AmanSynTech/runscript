pipeline {
    agent any
    environment {
        BASE_DIR = '/home/aman/NetBeansProjects/FirstAutomation/'
    }
    stages {
        stage('Running Login') {
            steps {
                echo "Running codes for login only"
                sh '''
                    cd ${BASE_DIR}
                    mvn test -Dheadless=true
                '''
            }
        }
    }
}
