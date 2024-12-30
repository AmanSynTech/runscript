pipeline {
    agent any
    environment {
        BASE_DIR = '/home/aman/NetBeansProjects/FirstAutomation/'
    }
    stages {
         stage('Running Appium') {
            steps {
                echo "Starting appium ...."
                sh '''
                    appium &
                '''
                sleep 5 // Give Appium some time to initialize
            }
        }
        stage('Running Emulator') {
            steps {
                echo "Starting emulator ...."
                sh '''
                    emulator -avd TestAVD -no-snapshot-load -no-window &
                    adb wait-for-device
                '''
                sleep 20 // Ensure the emulator has fully booted
            }
        }
        stage('Running Test Script') {
            steps {
                echo "Running codes for login only ..."
                sh '''
                    cd ${BASE_DIR}
                    mvn test -Dheadless=true
                '''
            }
        }
    }
    post {
        always {
            echo "Cleaning up resources..."
            sh '''
                adb -s emulator-5554 emu kill || true
                pkill -f appium || true
            '''
        }
    }
}
