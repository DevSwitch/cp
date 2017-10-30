def srcdir = 'github.com/jakecoffman/cp'

pipeline {
    agent {
        docker {
            image 'golang'
        }
    }

    stages {
        stage('Setup') {
            steps {
                sh "mkdir -p \$GOPATH/src/$srcdir"
                sh "ln -s . \$GOPATH/src/$srcdir"
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
