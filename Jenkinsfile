pipeline {
  agent any
  stages {
    stage('Checkout') {
       steps {
         git url: 'https://github.com/Hanskuy/sast-demo-app', branch:
'master'
       }
    }
    stage('Install Dependencies') {
      steps {
        sh '''
         python3 -m venv venv
         . venv/bin/activate
         pip install --upgrade pip
         pip install bandit
        '''
      }
    }
    stage('SAST Analysis') {
      steps {
        sh '''
         . venv/bin/activate
         bandit -f xml -o bandit-output.xml -r . || true
        '''
      }
    }
  }
}
