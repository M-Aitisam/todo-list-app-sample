pipeline {
   agent any 
   stages {
      stage('Checkout Code') {
        steps {
          echo 'Code sucessfully pulled form Github!'
        }
      stage('Build Docker Image') {
        steps {
          echo 'Building the todo-app Docker Image........'
          bat 'docker build . -t todo-pipeline-app'
        }
      }
      stage('Run New Container') {
        steps {
          echo 'Starting the new Container in  port 3000'
          bat 'docker run -p 3000:3000 -d --name todo-pipeline-container todo-pipeline-app'
          
        }
      }  
    }    
    post {
      always {
        echo 'Pipeline execution finished!'
      }  
    } 
}    
