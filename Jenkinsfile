pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/4kanksh/jenkins-demo.git',
                    branch: 'main'
            }
        }

        stage('Run script') {
            steps {
                sh 'chmod +x script.sh'
                sh './script.sh'
            }
        }
    }
     post {

        success {
            emailext (
                subject: "SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build succeeded!\nCheck: ${BUILD_URL}",
                to: "akanksh.jpg@gmail.com"
            )
        }

        failure {
            emailext (
                subject: "FAILED: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build failed!\nCheck: ${BUILD_URL}",
                to: "akanksh.jpg@gmail.com"
            )
        }
    }
}
