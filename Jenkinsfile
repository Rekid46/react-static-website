pipeline {
    agent {
        label 'slave1'
    }
    stages {
        stage("Build") {
            steps {
                sh "rm -r /home/jenkins/workspace/Frontend/build"
                sh "export NODE_OPTIONS=--max_old_space_size=8192"
                sh "npm install --save --legacy-peer-deps"
                sh "npm run build"
            }
        }
        stage("Deploy") {
            steps {
                sh "rm -r /var/www/html/frontend/*"
                sh "mv /home/jenkins/workspace/Frontend/build/* /var/www/html/frontend"
            }
        }
    }
}
