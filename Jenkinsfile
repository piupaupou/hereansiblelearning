pipeline {
    agent none 
  
    parameters {
      string defaultValue: 'Настя', name: 'student_name', trim: true
    }

    triggers {
      pollSCM '*/3 * * * *'
    }

    stages {
      stage('Main') {
        agent {
          docker {
            image 'python:latest'
          }
        } 
        steps {
          sh 'pip install -r requirements.txt'
          sh 'python hello.py --name ${student_name} > result.txt'
          archiveArtifacts artifacts: 'result.txt', followSymlinks: false
        }
      }
    }
}
