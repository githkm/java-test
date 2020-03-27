pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
            echo "${JOB_NAME} is Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            // Get some code from a GitHub repository
            //git branch: 'master', credentialsId: '888451db-2e9d-41a0-9214-8cf81f444260', url: 'git@github.com:githkm/java-test.git'  
            }
        }
        stage('Build') {
            steps {
             // Run Maven on a Unix agent.
             sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('test') {
            steps {
            sh "echo test..."
            sh "pwd"
            }
            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                junit 'target/surefire-reports/*.xml'
                archiveArtifacts 'target/*.jar'
                }
            }
        }
        stage('deploy') {
            steps {
            sh "echo deploy..."
            sh "[ -f ${JOB_NAME}/${env.BRANCH_NAME} ] || mkdir /data/images/${JOB_NAME}/${env.BRANCH_NAME}/ -p "
            sh "mv -f target/*.jar /data/images/${JOB_NAME}/${env.BRANCH_NAME}/"
            }
        }
    }
}
