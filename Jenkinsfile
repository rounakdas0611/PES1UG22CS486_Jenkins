pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh '''
                    mkdir -p main
                    if [ ! -f "main/hello.cpp" ]; then
                        echo "ERROR: main/hello.cpp not found in workspace!"
                        ls -R
                        exit 1
                    fi
                    g++ nonexistent_file.cpp -o main/hello_exec
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Testing the project...'
                sh '''
                    if [ ! -f "main/hello_exec" ]; then
                        echo "ERROR: Executable file missing!"
                        exit 1
                    fi
                    ./main/hello_exec
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
