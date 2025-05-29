pipeline {
    agent any

    environment {
        // Disable host key checking to avoid SSH prompts
        ANSIBLE_HOST_KEY_CHECKING = 'False'
        // Ensure npm and ansible are found in PATH
        PATH = "/usr/bin:/usr/local/bin:$PATH"
    }

    stages {
        stage('Clone Repository') {
            steps {
                checkout scm
            }
        }

        stage('Install Node.js Dependencies') {
            steps {
                echo 'Installing npm packages...'
                sh 'npm install'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                echo 'Running Ansible deployment...'
                sh 'ansible-playbook -i inventory playbook.yml'
            }
        }
    }

    post {
        failure {
            echo '❌ Build failed. Check the logs above for details.'
        }
        success {
            echo '✅ Build completed successfully!'
        }
    }
}
