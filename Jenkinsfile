pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '1', artifactNumToKeepStr: '2', daysToKeepStr: '1', numToKeepStr: '5')
  }
  triggers {
  eventTrigger(simpleMatch('testingCompleted'))
}
  stages {
    stage('Received an event') {
      steps {
        sh 'echo \'I just received a testingCompleted event\''
      }
    }
  }
}
