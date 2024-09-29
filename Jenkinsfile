pipeline {
    agent {
        docker {
            image 'node:20.2.0-alpine3.17'
            args '-p 3000:3000'
        }
    }
  
    stages {
        
        stage('Checkout') {
            steps {
                // Faz o checkout do repositório
                checkout scm
            }
        }
        stage('Build') {
            steps {
                 // Remover node_modules e package-lock.json
                sh 'rm -rf node_modules package-lock.json || true'
                // Instalar dependências
                sh 'npm install'
                sh 'CI=false npm run build'
            }
        }
    }
}
