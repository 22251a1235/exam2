pipeline { 
    agent any 
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning Repo' 
                git url : "https://github.com/22251a1235/exam2.git"
                branch : 'master'
            }
        }
        stage('Build') {
            steps {
                echo 'Build Docker Image'
                bat 'docker build -t mywebapp .'
            }
        }
        stage('Run') {
            echo 'Running a container'
            bat 'docker rm -f mycontainer || exit 0'
            bat 'docker run -d -p 5000:5000 --name mycontainer mywebapp'
        }
    }
    post {
        success {
            echo 'Build successful'
        }
        failure {
            echo 'Build failed'
        }
    }
}