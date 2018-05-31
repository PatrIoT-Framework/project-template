pipeline {
    agent {
        label 'maven-docker'
    }

    stages {

        stage('Wait') {
            steps {
                sh 'sleep 60'
            }
        }

        stage('Checkstyle') {
            steps {
                sh '''
                 mvn site
                '''
            }
            post {
                always {
                    checkstyle canComputeNew: false, canRunOnFailed: true, defaultEncoding: '', healthy: '20', pattern: '**/checkstyle-result.xml', shouldDetectModules: true, thresholdLimit: 'high', unHealthy: '50'
                }
            }

        }

        stage('Test') {
            steps {
                sh '''
                  mvn test
                '''
            }
        }
    }
}
