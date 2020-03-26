node {
    stage('checkout') {
        // Get some code from a GitHub repository
        git credentialsId: '888451db-2e9d-41a0-9214-8cf81f444260', url: 'git@github.com:githkm/java-test.git'  
    }
    stage('Build') {
       // Run Maven on a Unix agent.
       sh "mvn -Dmaven.test.failure.ignore=true clean package"
    }
    stage('test') {
        sh "echo test..."
    }
    stage('deploy') {
        sh "echo deploy..."
    }
}
