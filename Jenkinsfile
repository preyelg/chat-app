pipeline {
  agent any

  environment {
    ANSIBLE_HOST_KEY_CHECKING = 'False'
    PATH = "/usr/local/bin:/usr/bin:/bin:$PATH"
  }

  stages {
    stage('Clone Repository') {
      steps {
        git branch: 'deployment-3', url: 'https://github.com/preyelg/chat-app.git'
      }
    }

    stage('Install Node.js Dependencies') {
      steps {
        echo '📦 Installing npm packages...'
        dir('files') {
          sh 'npm install'
        }
      }
    }

    stage('Run Ansible Playbook') {
      steps {
        echo '🚀 Running Ansible deployment...'
        sh 'ANSIBLE_CONFIG=./ansible.cfg ansible-playbook -i inventory playbook.yml'
      }
    }
  }

  post {
    success {
      echo '✅ Build and deployment completed!'
    }
    failure {
      echo '❌ Build failed. Check above for error details.'
    }
  }
}
