pipeline {
    agent {
        docker { 
            image 'cloudcustodian/c7n'
            args '--entrypoint=\'\''
        }
    }
    stages {
        stage('Load virtualenvironment') {
            steps {
                sh "echo $PATH"
            }
        }
        stage('Test') {
            steps {
                sh "AWS_DEFAULT_REGION=us-west-1 custodian run --output-dir=. check-empty-tag.yml"
            }
        }
    }
}
