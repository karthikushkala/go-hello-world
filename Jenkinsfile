pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        docker {
          image 'golang'
        }

      }
      steps {
        sh 'cd ${GOPATH}/src'
        sh 'mkdir -p ${GOPATH}/src/hello-world'
        sh 'cp -r ${WORKSPACE}/* ${GOPATH}/src/hello-world'
        sh 'cd /go/src/hello-world'
        sh 'ls -la'
        sh 'go build'
      }
    }

    stage('Test') {
      agent {
        docker {
          image 'golang'
        }

      }
      steps {
        sh 'cd ${GOPATH}/src'
        sh 'mkdir -p ${GOPATH}/src/hello-world'
        sh 'cp -r ${WORKSPACE}/* ${GOPATH}/src/hello-world'
        sh 'go clean -cache'
        sh 'go test ./... -v -short'
      }
    }

  }
  environment {
    GOCACHE = '/tmp'
  }
}