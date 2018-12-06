#!groovy

import groovy.json.JsonOutput

node {
  
  try {
    
    stage 'pre-check'
    sh 'ls -altr'
    sh 'pwd'
    
    stage 'checkout'
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '47c580f2-2468-427d-b95b-9ad4fd15e472', url: 'https://github.com/sxudop/CBJ.git']]])
    version = sh (
      script: 'echo "v-$(git rev-parse --short HEAD)"',
      returnStdout: true
      ).trim()
    
    stage 'post-check'
    sh 'ls -altr'
    sh 'pwd'
    
    currentBuild.result = "SUCCESS"  
    currentBuild
    
  }
  catch(e) {
    
    //stage 'cleanup'
    // sh 'ls -altr'
    // deleteDir() /* clean up our workspace */
    currentBuild.result = "FAILURE"
    throw e
    }
    
  echo "FINAL RESULT: ${currentBuild.result}"   
}
