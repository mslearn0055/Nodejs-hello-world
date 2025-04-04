@Library('jenkins-shared-libraries') _
pipeline {
    agent any
    // tools { nodejs "nodejs" }  // ✅ Correct

    stages {
        stage('Clone Repository'){
            steps {
                git branch: 'main', url: 'https://github.com/mslearn0055/Nodejs-hello-world.git'
            }
        }
        stage('Install Dependencies'){
            steps {
                npmInstall()
            }
        }
        stage('Perform API testing'){
            steps {
                sh 'npm test'
            }
        }
        stage('Start Application'){
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
