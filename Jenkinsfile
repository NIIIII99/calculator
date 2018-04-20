pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat(script: 'gradlew.bat clean assemble', returnStatus: true, returnStdout: true)
      }
    }
    stage('Package') {
      steps {
        bat(script: 'gradlew.bat build', returnStatus: true, returnStdout: true)
      }
    }
    stage('Docker Build') { 
      steps {
        bat 'docker build -t han/calculator -f dockerfile . '
        //sh "docker build -t com/calculator ."
      }
    }     
  }
}
