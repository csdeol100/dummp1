node {
    
    stage('Checkout SCM') {
        git branch: 'master', credentialsId: 'githubs', url: 'https://github.com/csdeol100/dummp1.git'
    }
    stage('Compile ') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
        sh ' mvn compile'
           //sh 'echo hello'
           sleep 5
        }
    }
    stage('Unit Test') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         sh 'mvn test'
           //sh 'echo test'
          // sleep 10
        }
    }
    stage('Publish Test Result') {
        junit '**/*.xml'
        //sh 'echo result'
        sleep 5
    }
    stage('Package') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         sh 'mvn package'
          //sh 'echo package'
        }
    }
    stage('Publish Artifact') {
        archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
    }
    stage('Slack'){
        slackSend channel: 'devops-nov-2020', color: 'red', message: "Project Name '${JOB_NAME}'  Build Number  '${BUILD_NUMBER}'"
    }
}
