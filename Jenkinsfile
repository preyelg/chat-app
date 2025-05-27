pipeline {
    agent any

    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Deploy with Ansible') {
            steps {
                bat '''
                    wsl ansible-playbook -i /mnt/c/Users/Ladei/OneDrive/Desktop/chat-app/inventory /mnt/c/Users/Ladei/OneDrive/Desktop/chat-app/playbook.yml
                '''
            }
        }
    }
}
