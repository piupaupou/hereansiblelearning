pipeline {
    agent none 
  
    parameters {
      string 'student_name'
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
          sh 'python hello.py --name ${params.student_name} > result.txt'
          archiveArtifacts artifacts: 'result.txt', followSymlinks: false
        }
      }
    }
}
