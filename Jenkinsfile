pipeline {
    agent any
    stages {
        stage('Deps') {
          steps {
              sh 'make deps'
              }
        }
        stage('Test') {
            steps {
              sh 'make test_xunit || true'
              step([$class: 'XUnitBuilder',
                thresholds: [
                  [$class: 'SkippedThreshold'. failureThreshold: '0'],
                  [$class: 'failedThreshold', failureThreshold: '1']],
                tools: [[$class: 'JUnitType', pattern: 'test_results.xml']]])
        	}
        }
    }
}
