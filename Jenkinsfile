pipeline {
  agent any
    
  tools {nodejs "NodeJS"}

  environment {
      CI = 'true'
      NODE_ENV = 'test'
  }
    
  stages {
        
    stage('Checkout SCM') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/dev']], userRemoteConfigs: [[url: 'https://github.com/andela/neon-ah-backend', poll: 'true']]])          
      }
    }
        
    stage('Build: Install Project Dependencies') {
      steps {
        sh 'npm install'
      }
    }
     
    stage('Run Test') {
      steps {
         sh 'npm test'
      }
    }      
  }

  post{
      always{
          echo "** Build Completed **"
      }
      success{
          echo "Result ==> Build was successful"
      }
      failure{
          echo "Result ==> Build Failed"
      }
  }
}
