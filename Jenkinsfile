pipeline {
    agent {
        docker {
            image 'golang'
        }
    }

    stages {
        stage('Setup') {
            steps {
                sh "mkdir -p \$GOPATH/src/github.com/jakecoffman"
                sh "ln -s . \$GOPATH/src/github.com/jakecoffman/cp"
            }
        }
        stage('Dependencies') {
            steps {
                sh 'go get ./...'
            }
        }
        stage('Build') {
            steps {
                sh 'go build ./...'
            }
        }
        stage('Test') {
            steps {
                sh 'go test ./...'
            }
        }
    }
}
