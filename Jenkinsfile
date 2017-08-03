pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean checkstyle:checkstyle package'
      }
    }
    stage('Test') {
      steps {
        junit(testResults: '**/build/test-reports/*.xml', allowEmptyResults: true)
        checkstyle(pattern: '**/target/checkstyle-result.xml')
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts(artifacts: '**/target/*.jar', allowEmptyArchive: true)
      }
    }
  }
}