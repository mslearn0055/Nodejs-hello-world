@Library('jenkins-shared-libraries') _
pipeline {
    agent any
    tools { nodejs "nodejs" }  

    environment {
        PATH = "/var/lib/jenkins/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/nodejs/bin:$PATH"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/mslearn0055/Nodejs-hello-world.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    npmInstall()  // Call the shared library function
                }
            }
        }
        stage('Perform API testing') {
            steps {
                sh 'npm test'
            }
        }
        stage('Start Application') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "pankaj"
            }
            steps {
                sh 'npm start'
            }
        }
    }
}
