pipeline {
    agent any
  
    parameters {
      string 'student_name'
    }

    triggers {
      pollSCM '*/3 * * * *'
    }

    stages {
      stage('Main') {
        steps {
          sh 'pip install -r requirements.txt'
          sh 'python hello.py --name $params.student_name > result.txt'
          archiveArtifacts artifacts: 'result.txt', followSymlinks: false
        }
      }
    }
}
