#!groovy
library identifier: 'JenkinsSharedLibrary@master', retriever: modernSCM(
        [$class: 'GitSCMSource',
         remote: 'https://github.com/ChhaviSharma-97/JenkinsSharedLibrary'])
pipeline {
   agent any
    options{
       timestamps()
       ansiColor('xterm')
   }
   stages {
      stage('List All Images') {
         steps {
             script{
                    sh ''' docker image ls
                    '''
                    ansicolor.info("Successfully Executed")
                    def ret = sh(script: 'dockker image ls', returnStatus: true)
                    ansicolor.warning(ret)
             }
         }
      }
      stage('Git Commit Id') {
         steps {
              script{
		    def gitId=sh(script:'git rev-parse HEAD', returnStdout: true)
                    ansicolor.gitCommitId(gitId)
             }
         }
      }
   }
}
