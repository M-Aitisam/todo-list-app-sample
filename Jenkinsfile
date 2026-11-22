pipeline {

    agent any 


    stages {
        
        stage('Checkout Code') {
            steps {
                echo 'Code successfully pulled from GitHub!'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building the todo-app Docker image...'
                bat 'docker build . -t todo-pipeline-app'
            }
        }
        
        stage('Cleanup Old Container') {
            steps {
                echo 'Removing old container if it exists...'
                bat 'docker rm -f todo-pipeline-container || exit 0'
            }
        }

        stage('Run New Container') {
            steps {
                echo 'Starting the new container on port 3000...'
                bat 'docker run -p 3000:3000 -d --name todo-pipeline-container todo-pipeline-app'
            }
        }
    }

    // 3. What to do after the pipeline finishes
    post {
        always {
            echo 'Pipeline execution finished!'
        }
    }
}
