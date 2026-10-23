pipeline {
    agent any

    parameters { choice (name: 'ENVIRONMENT' ,
                         choices: ['dev','staging','production']) }
    stages {
        stage('approve') {
            when { expression { params.ENVIRONMENT == 'production' } }
            steps { input message: 'Deploy to production?' }
        }
        stage('Deploy') {
            steps { bat "echo Deploy to ${params.ENVIRONMENT}" }
        }
    }
}
