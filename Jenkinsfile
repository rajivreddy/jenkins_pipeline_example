def generator = { String alphabet, int n ->
  new Random().with {
    (1..n).collect { alphabet[ nextInt( alphabet.length() ) ] }.join()
  }
}


node {
  dev token_data = generator( (('A'..'Z')+('0'..'9')).join(), 16 )
 properties([
  pipelineTriggers([
   [$class: 'GenericTrigger',
    genericVariables: [
     [key: 'ref', value: '$.ref']
    ],


    causeString: 'Triggered on $ref',

    token: '$token_data',
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
