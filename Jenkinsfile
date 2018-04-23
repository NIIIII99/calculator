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
        bat 'docker build -t han_calculator -f dockerfile . '
        //sh "docker build -t com/calculator ."
      }
    }
    stage('Docker Image registry'){
      steps {
        bat 'docker tag han_calculator:latest localhost:5000/han_calculator:latest
        bat 'docker push localhost:8888/han/calculator'
      }
    }
  }
}
