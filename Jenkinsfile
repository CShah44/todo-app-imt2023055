pipeline {
    agent any
    
    environment {
        // REPLACE 'dockerhub-credentials-id' with the ID you gave your credentials in Jenkins
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials-id') 
        
        // REPLACE 'YOUR_ROLL_NUMBER' with your Docker Hub username/roll number
        DOCKER_IMAGE = 'greatwarrior44/imt2023055-todo-app' 
        
        REGISTRY_TAG = "build-${BUILD_NUMBER}"
    }
    
    stages {
        stage('Build & Install Dependencies') {
            steps {
                script {
                    echo 'Installing dependencies...'
                    if (isUnix()) {
                        sh 'pip install -r todo-app/requirements.txt'
                    } else {
                        bat 'pip install -r todo-app/requirements.txt'
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    // Using python -m pytest to ensure we use the installed module
                    // Adding PYTHONPATH to ensure imports work correctly
                    if (isUnix()) {
                        sh 'export PYTHONPATH=$PYTHONPATH:$(pwd)/todo-app && python -m pytest todo-app/tests'
                    } else {
                        // Windows set PYTHONPATH
                        bat 'set PYTHONPATH=%CD%\\todo-app && python -m pytest todo-app/tests'
                    }
                }
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    echo 'Building Docker image...'
                    if (isUnix()) {
                        sh "docker build -t ${DOCKER_IMAGE}:${REGISTRY_TAG} ./todo-app"
                        sh "docker tag ${DOCKER_IMAGE}:${REGISTRY_TAG} ${DOCKER_IMAGE}:latest"
                    } else {
                        bat "docker build -t %DOCKER_IMAGE%:%REGISTRY_TAG% ./todo-app"
                        bat "docker tag %DOCKER_IMAGE%:%REGISTRY_TAG% %DOCKER_IMAGE%:latest"
                    }
                }
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                script {
                    echo 'Pushing to Docker Hub...'
                    if (isUnix()) {
                        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                        sh "docker push ${DOCKER_IMAGE}:${REGISTRY_TAG}"
                        sh "docker push ${DOCKER_IMAGE}:latest"
                    } else {
                        bat 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
                        bat "docker push %DOCKER_IMAGE%:%REGISTRY_TAG%"
                        bat "docker push %DOCKER_IMAGE%:latest"
                    }
                }
            }
        }
    }
    
    post {
        always {
            script {
                echo 'Cleaning up...'
                if (isUnix()) {
                    sh 'docker logout'
                } else {
                    bat 'docker logout'
                }
            }
        }
    }
}
