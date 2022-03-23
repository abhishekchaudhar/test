pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'bulding some code'
          }
        }

        stage('Test') {
          steps {
            echo 'testing some code'
            echo "Get the driver path ${driverpath}"
          }
        }

        stage('Test log') {
          environment {
            localHost = 'Reverse proxy'
          }
          steps {
            writeFile(file: 'logfiletest.txt', text: "This location of driver is ${driverpath} and the name of server is ${localHost}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Deploy') {
          steps {
            input(message: 'Do you want to deploy', id: 'ok')
            echo 'Deploying code on servers'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts 'logfiletest.txt'
          }
        }

      }
    }

  }
  environment {
    driverpath = 'cd /home/vagrant/Tomcat'
  }
}