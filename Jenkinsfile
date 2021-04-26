pipeline {
  agent any
  triggers {
    GenericTrigger(
     genericVariables: [
      [key: 'ref', value: '$.ref']
     ],

     token: 'abc123',
     
     causeString: 'Triggered on $ref',
     
     printContributedVariables: true,
     printPostContent: true,
    
     regexpFilterText: '$ref',
     regexpFilterExpression: 'refs/heads/master|refs/heads/dev|refs/heads/stage'
    )
  }
  stages {
    stage('Some step') {
      steps {
        sh "echo $ref"
      }
    }
  }
}
