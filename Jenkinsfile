node {
    
    stage('Checkout SCM') {
        git branch: 'dev', credentialsId: 'githubs', url: 'https://github.com/atinsingh/dummp1.git'
    }
    stage('Compile ') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         //sh 'mvn compile'
           sh 'echo hello'
           sleep 5
        }
    }
    stage('Unit Test') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         //sh 'mvn Test'
           sh 'echo test'
           sleep 10
        }
    }
    stage('Publish Test Result') {
        //junit '**/*.xml'
        sh 'echo result'
        sleep 5
    }
    stage('Package') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         //sh 'mvn package'
          sh 'echo package'
        }
    }
    stage('Publish Artifact') {
        //archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
    }
    stage('Slack'){
       // slackSend channel: 'Charandeep Deol'
        slackSend  teamDomain: 'pragraconsulting2020', tokenCredentialId: 'slack' , message: 'Build Successful '${JOB_NAME}' , Build Number '${BUILD_ID}''
    }
}
