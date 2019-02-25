pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World, Build stage"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }        
        stage('Test') {
            steps {
                sh 'echo "Test stage"; exit 0'
            }
        }
        stage('Deploy') {
            steps {
                timeout(time: 3, unit: 'MINUTES') {
                    retry(2) {
                        sh 'echo "Deploying stage"'
                    }
                }
            }
        }        
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
