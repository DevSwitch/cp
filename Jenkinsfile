def src='\$GOPATH/src/github.com/jakecoffman/cp'

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
                sh "ln -s `pwd` $src"
            }
        }
        stage('Dependencies') {
            steps {
                dir(src) {
                    sh 'go get ./...'
                }
            }
        }
        stage('Build') {
            steps {
                dir(src) {
                    sh 'go build ./...'
                }
            }
        }
        stage('Test') {
            steps {
                dir(src) {
                    sh 'go test ./...'
                }
            }
        }
    }
}
