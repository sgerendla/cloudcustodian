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
                sh "AWS_DEFAULT_REGION=us-west-1 c7n run -v -s --output-dir=. check-empty-tag.yml"
            }
        }
    }
}
