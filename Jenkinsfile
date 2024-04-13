pipeline {
    agent any
    
    stages {
        stage('Checkout App') {
            steps {
                script {
                    sshagent(credentials: ['devopslab-cred']) {
                        sh 'ssh -o StrictHostKeyChecking=no devopslab@172.17.14.121 "if [ -d /home/devopslab/Devtron-pipeline-ssh-POC ]; then cd /home/devopslab/Devtron-pipeline-ssh-POC && git pull origin main; else git clone -b main https://github.com/bhavikp-icpl/Devtron-pipeline-ssh-POC.git; fi"'
                    }
                }
            }
        }
        stage('Pipeline triggered for SSH into another VM') {
            steps {
                script {
                    sshagent(credentials: ['devopslab-cred']) {
                        sh 'ssh -o StrictHostKeyChecking=no devopslab@172.17.14.121 "cd /home/devopslab/Devtron-pipeline-ssh-POC/code && python3 hello-world.py"'
                    }
                }
            }
        }
    }
}
