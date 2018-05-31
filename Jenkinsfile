node {

    stage ('Test') {
        sh '''
        mvn clean test
        '''
    }

    stage ('Check Style') {
    sh '''
    mvn site
    '''
    }

}