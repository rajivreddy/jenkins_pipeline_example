node {
  def verCode = UUID.randomUUID().toString()
 properties([
  pipelineTriggers([
   [$class: 'GenericTrigger',
    genericVariables: [
     [key: 'ref', value: '$.ref'],
     [
      key: 'https_url',
      value: 'clone_url',
     ]
    ],


    causeString: 'Triggered on $ref',

    token: verCode,
    tokenCredentialId: '',

    printContributedVariables: true,
    printPostContent: true,

    silentResponse: false,

    regexpFilterText: '$ref',
    regexpFilterExpression: 'refs/heads/master$|refs/heads/dev$|refs/heads/stage$'
   ]
  ])
 ])
}


pipeline {
  def last = ref.tokenize('.').last()
  agent any
  stages {
    stage('Some step') {
      steps {
        sh "Branch Name is echo $ref"
        sh "Repo URL is $clone_url"
      }
    }
  }
}
