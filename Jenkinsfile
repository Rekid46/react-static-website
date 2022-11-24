pipeline {
    agent {
        ubuntu {
            label 'slave1'
        }
    }
    stages {
        stage("Build") {
            steps {
                sh "sudo rm -r /home/jenkins/workspace/Frontend/build"
                sh "export NODE_OPTIONS=--max_old_space_size=8192"
                sh "sudo npm install --save --legacy-peer-deps"
                sh "sudo npm run build"
            }
        }
        stage("Deploy") {
            steps {
                sh "sudo rm -r /var/www/html/frontend/*"
                sh "sudo mv /home/jenkins/workspace/Frontend/build/* /var/www/html/frontend"
            }
        }
    }
}
