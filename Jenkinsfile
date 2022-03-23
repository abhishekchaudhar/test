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
            echo '"Get the driver path ${driverpath}"'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying code on servers'
      }
    }

  }
  environment {
    driverpath = 'cd /home/vagrant/Tomcat'
  }
}