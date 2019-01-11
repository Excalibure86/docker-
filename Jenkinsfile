pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        build(wait: true, job: 'build', propagate: true, quietPeriod: 10)
        error 'defeaf'
      }
    }
    stage('zfergf') {
      steps {
        archiveArtifacts(allowEmptyArchive: true, artifacts: 'egrgtg')
      }
    }
  }
}