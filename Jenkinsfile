pipeline {
    agent any

    parameters {
        choice(name: 'action', choices: ['create', 'update', 'delete'], description: 'Select an action')
        string(name: 'channel', defaultValue: '', description: 'Enter the slack channel')
        password(name: 'webhook', defaultValue: '', description: 'Enter the webhook url')
    }

    stages {
        stage('Create AWS Secret') {
            steps {
                script {
                    def secretCommand

                    if (params.action == 'create') {
                        secretCommand = 'add'
                    } else if (params.action == 'update') {
                        secretCommand = 'update'
                    } else if (params.action == 'delete') {
                        secretCommand = 'delete'
                    } else {
                        error("Invalid action: ${params.action}")
                    }

                    withCredentials([string(credentialsId: 'aws-credentials', variable: 'awsCredentials')]) {
                        sh """
                            aws secretsmanager ${secretCommand}-secret --secret-id ${params.channel} --secret-string '${params.webhook}' --region us-east-1
                        """
                    }
                }
            }
        }
    }
}
