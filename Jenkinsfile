pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                // Replace the local path with the GitHub repository URL
                git 'https://github.com/eliaise/owaspdependencytest.git'
            }
        }

        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
            }
        }
    }    
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
