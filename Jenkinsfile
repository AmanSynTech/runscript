pipeline {
    agent any
    environment {
        BASE_DIR = '/home/aman/inventory-testing-clone/DockerBuild'
    }
    stages {
        stage('Running Base Ubuntu') {
            steps {
                echo "Creating ubuntu as base..."
                sh '''
                    cd ${BASE_DIR}/1_BaseUbuntu
                    make
                '''
            }
        }
        stage('Running Install Packages') {
            steps {
                echo "*** Installing all the required packages ***"
                sh '''
                    cd ${BASE_DIR}/2_InstallPackages
                    make
                '''
            }
        }
        stage('Running Install SDK') {
            steps {
                echo "*** Installing SDK ***"
                sh '''
                    cd ${BASE_DIR}/3_InstallSDK
                    make
                '''
            }
        }
        stage('Running Create Emulator') {
            steps {
                echo "*** Creating required Emulator ***"
                sh '''
                    cd ${BASE_DIR}/4_CreateEmulator
                    make
                '''
            }
        }
        stage('Running Install Netbeans') {
            steps {
                echo "*** Installing required Netbeans App ***"
                sh '''
                    cd ${BASE_DIR}/5_InstallNetbeans
                    make
                '''
            }
        }
        stage('Running Install inventory Server') {
            steps {
                echo "*** Installing required Inventory Server ***"
                sh '''
                    cd ${BASE_DIR}/6_InstallInvServer
                    make
                '''
            }
        }
        stage('Building Scripts nad Installing App for Automation') {
            steps {
                echo "*** Building all the automation test scripts and installing app for headless testing ***"
                sh '''
                    cd ${BASE_DIR}/7_RunScript
                    make
                '''
            }
        }
        stage('Running Test Scripts for Automation') {
            steps {
                echo "*** Running all the automation test scripts for headless testing ***"
                sh '''
	                docker run --device /dev/kvm -t -e file=TestNG pivotech-appiumrun:v1.0            
                '''
            }
        }
    }
}
