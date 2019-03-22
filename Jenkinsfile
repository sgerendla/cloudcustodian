pipeline {
    agent {
        docker { image 'node:7-alpine' }
    }
    stages {
        stage('Setup VirtualEnvironment')
        {
            sh "mkdir /app && cp -a . /app && cd /app && virtualenv --no-site-packages -p python2.7 ."
        }
        stage('Install Cloudcustodian') {
            sh "cd /app && . bin/activate && pip install c7n"
        }
        stage('Test') {
            sh "AWS_DEFAULT_REGION=us-west-1 custodian run --output-dir=. check-empty-tag.yml"
        }
    }
}
