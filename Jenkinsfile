pipeline {
    agent any
    
    environment {
        BUILD_FILE_NAME = 'laptop.txt'
    }

    stages {
        stage('Build') {
            steps {
                cleanWs()
                echo 'Building Laptop'
                sh '''
                mkdir -p build
                touch build/$BUILD_FILE_NAME
                echo "Motherboard" >> build/$BUILD_FILE_NAME
                cat build/$BUILD_FILE_NAME
                #rm  build/$BUILD_FILE_NAME
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing New Laptop'
                sh 'test -f build/$BUILD_FILE_NAME'
            }
        }
    }
    
    post {
        success {
            archiveArtifacts artifacts: 'build/**'
        }
    }
}