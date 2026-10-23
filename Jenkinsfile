pipeline {
    agent any

    parameters { choice (name: 'ENVIRONMENT' ,
                         choices: ['dev','staging','production']) }
    stages {
        stage ('Checkout') {steps {checkout scm } }
        stage('Quality') {parallel {
            stage('Build') { steps { bat 'echo Build'} }
             stage('Lint') { steps { bat 'echo Lint'} } } }
             stage('Test') { steps { bat 'echo Test'} } 
             stage('Package') { steps { bat 'echo Package'} }
    }
}
        stage('approve') {
            when { expression { params.ENVIRONMENT == 'production' } }
            steps { input message: 'Deploy to production?' }
        }
        stage('Deploy') {
            steps { bat "echo Deploy to ${params.ENVIRONMENT}" }
        }
    }
}
