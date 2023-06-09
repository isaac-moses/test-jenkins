pipeline {
    agent {
        label 'baseimage'
    }
    parameters {
        choice(name: 'action', choices: ['create', 'update', 'delete'], description: 'Select an action')
        string(name: 'channel', defaultValue: '', description: 'Enter the channel')
        password(name: 'webhook', defaultValue: '', description: 'Enter the webhook')
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

                    echo "Action: ${params.action}"
                    echo "Channel: ${params.channel}"
                    echo "Webhook: ${params.webhook}"
                }
            }
        }
    }
}
