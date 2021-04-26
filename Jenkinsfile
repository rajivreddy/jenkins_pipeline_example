node {
  def verCode = UUID.randomUUID().toString()
 properties([
  pipelineTriggers([
   [$class: 'GenericTrigger',
    genericVariables: [
     [key: 'ref', value: '$.ref']
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
  agent any
  stages {
    stage('Some step') {
      steps {
        sh "echo $ref"
      }
    }
  }
}
